using System;
using System.Collections.Generic;

class Book
{
    public string Title;
    public string Author;
    public string ISBN;

    private bool isAvailable = true;

    public Book(string title, string author, string isbn)
    {
        Title = title;
        Author = author;
        ISBN = isbn;
    }

    public void BorrowBook()
    {
        if (isAvailable)
        {
            isAvailable = false;
            Console.WriteLine(Title + " kitabi goturuldu.");
        }
        else
        {
            Console.WriteLine(Title + " kitabi artiq goturulub.");
        }
    }

    public void ReturnBook()
    {
        isAvailable = true;
        Console.WriteLine(Title + " kitabi qaytarildi.");
    }

    public void ShowInfo()
    {
        string status;

        if (isAvailable)
            status = "Movcuddur";
        else
            status = "Goturulub";

        Console.WriteLine("Kitab: " + Title);
        Console.WriteLine("Muellif: " + Author);
        Console.WriteLine("ISBN: " + ISBN);
        Console.WriteLine("Status: " + status);
        Console.WriteLine();
    }
}

class Program
{
    static void Main()
    {
        List<Book> library = new List<Book>();

        library.Add(new Book("Book 1", "Writer a", "111"));
        library.Add(new Book("Book 2", "Writer c", "222"));
        library.Add(new Book("Book 3", "Writer c", "333"));
        library.Add(new Book("Book 4", "Writer d", "444"));
        library.Add(new Book("Book 5", "Writer e", "555"));

        library[0].BorrowBook();
        library[2].BorrowBook();

        Console.WriteLine("\nKitabxanadaki kitablar:\n");

        foreach (Book book in library)
        {
            book.ShowInfo();
        }
    }
}
