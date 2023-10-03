using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Threading.Tasks;

namespace CTDLBAI4
{
    internal class IntNode
    {

        private int data;
        private IntNode next;


        //public int Frist { get => frist; set => frist = value; }
        //public int Last { get => last; set => last = value; }


        public int Data
        {
            get { return Data; }
            set { Data = value; }
        }

        public IntNode Next
        {
            get { return Next; }
            set { Next = value; }
        }

        public IntNode(int x = 0)
        {
            Data = x;
            Next = null;
        }
    }
}


using System;
using System.Collections.Generic;
using System.Diagnostics;
using System.Linq;
using System.Text;
using System.Threading.Tasks;

namespace CTDLBAI4
{
    internal class MyList
    {
        private IntNode first;
        private IntNode last;

        public MyList()
        {
            first = null;
            last = null;
        }

        internal IntNode First1 { get => first; set => first = value; }
        internal IntNode Last { get => last; set => last = value; }


        public bool IsEmty()
        {
            return first == null;
        }

        public void AddLast(IntNode newNode)
        {
            if (IsEmty())
                first = last = newNode;

            else
            {
                newNode.Next = first;
                first = newNode;
            }
            
        }
        public void AddFirst(IntNode NewNode)
        {
            if (IsEmty())
            {
                first = last = NewNode;
            }
            else
            {
                NewNode.Next = first;
                first = NewNode;
            }
        }


        public void Input()

        {
            int x;
            do

            {
                Console.Write("Gia tri (0 ket thuc): ");
                int.TryParse(Console.ReadLine(), out x);
                if (x == 0)
                    break;
        
                IntNode newNode = new IntNode(x);
                AddFirst(newNode);
            }
            while (true);
        }

        public MyList GetOddList(MyList list)
        {
            
            // Khởi tạo danh sách mới
            MyList oddList = new MyList();

            // Duyệt danh sách ban đầu
            for (IntNode node = list.First1; node != null; node = node.Next)
            {
                // Kiểm tra phần tử là số lẻ
                if (node.Data % 2 == 1)
                {
                    // Thêm phần tử vào danh sách mới
                    oddList.AddFirst(new IntNode(node.Data));
                }
            }

            // Trả về danh sách mới
            return oddList;
        }

        public MyList GetEvenlsit()
        {
            MyList kq = new MyList();
            for (IntNode p = first; p != null; p = p.Next)
            {
                if (p.Data % 2 == 0)
                {
                    kq.AddFirst(new IntNode(p.Data));
                }
            }
            return kq;
        }

        public IntNode Search(int x)
        {
            for (IntNode p = first; p != null; p = p.Next)
            {
                if (p.Data == x)
                {
                    return p;
                }
            }
            return null;
        }

        public void ShowList()
        {
            IntNode P = first;
            while (P != null)
            {
                Console.Write("{0} ->", P.Data);
                P = P.Next;
            }
            Console.WriteLine("null");
        }

        public IntNode Max()
        {
            IntNode pMax = first;
            for (IntNode p = first.Next; p != null; p = p.Next)
                if (p.Data > pMax.Data)
                    pMax = p;
            return pMax;

        }
    }
}


using System;
using System.Collections;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Threading.Tasks;

namespace CTDLBAI4
{
    internal class Program
    {
        static void TestInput()
        {
            MyList list = new MyList();
            list.Input();
            Console.WriteLine("DSLK so nguyen:");
            list.ShowList();
        }

        static void TestTimX()
        {
            int x;
            MyList list = new MyList();
            list.Input();
            Console.WriteLine("danh sach lien ket so nguyen :");
            list.ShowList();
            Console.WriteLine("gia tir can tim = ");
            int.TryParse(Console.ReadLine(), out x);
            IntNode kq = list.Search(x);
            if (kq == null)
                Console.WriteLine("khong ton tai " + x);
            else
                Console.WriteLine(" ton tai " + x);
        }

        static void TestTimMax()
        {
            MyList list = new MyList();
            list.Input();
            Console.WriteLine("danh sach lien ket so nguyen: ");
            list.ShowList();
            IntNode pMax = list.Max();
            Console.WriteLine(" gia tri lon nha = " + pMax.Data);

        }
        static void TestTaoDSChan()
        {
            MyList list = new MyList();
            list.Input();
            Console.WriteLine("danh sach lien ket so nguyen: ");
            list.ShowList();

            MyList kq = list.GetEvenlsit();
            Console.Write("DS ket qua: ");
            kq.ShowList();

        }



        static void Main(string[] args)
        {
            TestInput();
            //TestTimMax();
            //TestTimX();
            //TestTaoDSChan();
        }
    }
}
