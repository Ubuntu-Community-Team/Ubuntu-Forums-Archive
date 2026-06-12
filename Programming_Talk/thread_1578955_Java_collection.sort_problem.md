---
title: "Java collection.sort problem"
date: 2010-09-21
forum: Programming Talk
---

### Post by Minky2k on 2010-09-21
Hi I'm having problems with java and the collections.sort method. I can't figure out how to sort an arraylist using the compareTo and Comparable interface. I've created the compareTo method and so on, but how do I sort an arraylist in another class.

I have created a book class and a CollectionOfBooks class, and implemented the Comparable in Book-class. But how do I sort the CollectionOfBooks arraylist?

When I try to sort it, it gives me the error "The method sort(List<T>, Comparator<? super T>) in the type Collections is not applicable for the arguments"

From what I understand, the Collection.sort uses a List and then takes as arguments the list that is to be sorted and then what comparable-method to be used?

I've added the code below to clarify what i mean =)

```
//Skapar skelett

package se.kth.labb3b;

import java.io.BufferedInputStream;
import java.io.FileInputStream;
import java.io.IOException;
import java.io.InputStream;
import java.io.ObjectInput;
import java.io.ObjectInputStream;
import java.io.Serializable;
import java.util.List;
import java.util.Scanner;

public class UserInterface implements Serializable {

	public static void main(String[] args) {
		UI ui = new UI();
		int running = 1;
		
	    //note the use of abstract base class references
	    
	    try{
	      //use buffering
	      InputStream file = new FileInputStream( "books.dat" );
	      InputStream buffer = new BufferedInputStream( file );
	      ObjectInput input = new ObjectInputStream ( buffer );
	      try{
	        //deserialize the List
	        List<Book> recoveredBooks = (List<Book>)input.readObject();
	        //display its data
	        for(Book book: recoveredBooks){
	          System.out.println("Recovered books: " + book);
	          ui.readBook(book);
	        }
	      }
	      finally{
	        input.close();
	      }
	    }
	    catch(ClassNotFoundException e){
	      e.printStackTrace();
	    }
	    catch(IOException e){
	      e.printStackTrace();
	      System.out.println("File books.dat wasn't found!");
	    }


		while (running == 1) {
			System.out.println("\nWelcome to Lars and Daniels bookrecord!\n\n" + 
					"1) Add a new book\n" + 
					"2) List all objects\n" +
					"3) Search\n" +
					"4) Write to file");
			
			Scanner scan = new Scanner(System.in);
			int answer = scan.nextInt();
			switch (answer) {
			case 1:
				ui.addBook();
				break;
			case 2:
				ui.getAllBooks();
				break;
			case 3:
				System.out.print("Search title: ");
				//ui.getBooksByTitle(scan.nextLine());
				break;
			case 4:
				ui.writeToFile();
				break;
			default:
				System.out.println("Fail");
				running = 0;
				break;

			}
		}

	}
}
```

```
package se.kth.labb3b;

import java.io.BufferedOutputStream;
import java.io.FileOutputStream;
import java.io.IOException;
import java.io.ObjectOutput;
import java.io.ObjectOutputStream;
import java.io.OutputStream;
import java.io.Serializable;
import java.util.ArrayList;
import java.util.List;
import java.util.Scanner;


public class UI implements Serializable {

	Book books;
	CollectionOfBooks cob = new CollectionOfBooks();

	public void addBook() {
		System.out.print("Book name: ");
		Scanner scan = new Scanner(System.in);
		String bookName = scan.nextLine();
		System.out.print("ISBN: ");
		int isbn = scan.nextInt();
		System.out.print("Edition: ");
		int edition = scan.nextInt();
		System.out.print("Price: ");
		double price = scan.nextDouble();
		ArrayList<Author> lista = new ArrayList<Author>();
		System.out.print("Numbers of authors: ");
		int numberOfAuthors = scan.nextInt();
		for (int i = 0; i <= numberOfAuthors; i++) {
			System.out.println("Author: ");
			lista.add(new Author(scan.nextLine()));
		}
		books = new Book(bookName, isbn, edition, price, lista);
		cob.addBook(books);

	}
	
	public void readBook(Book book){
		cob.addBook(book);
	}

	/*public void getBooksByTitle(String bookname) {
		List<Book> temp = cob.remoteSort();
		Collections.sort(temp);
		System.out.println("Book:");
		String tempbook = Collections.binarySearch(temp, bookname);
		System.out.println(tempbook);

	}*/
	
	public void getAllBooks() {
		System.out.println("Book titles:");
		for (int j = 0; j < cob.getNumberOfBooks(); j++) {
			System.out.print(cob.toString(j));
		}

	}
	
	public void writeToFile(){
		List<Book> temp = cob.remoteSort();
	    try{
	        //use buffering
	        OutputStream file = new FileOutputStream( "books.dat" );
	        OutputStream buffer = new BufferedOutputStream( file );
	        ObjectOutput output = new ObjectOutputStream( buffer );
	        try{
	          output.writeObject(temp);
	        }
	        finally{
	          output.close();
	        }
	      }  
	      catch(IOException e){
	        e.printStackTrace();
	      }

	}
	
}

```

```

package se.kth.labb3b;

import java.util.ArrayList;
import java.util.Collections;
import java.util.List;

public class CollectionOfBooks {
	
	private ArrayList<Book> Books = new ArrayList<Book>();

	public void addBook(Book book) {
		Books.add(book);
	}

	public void removeBook(Book book) {
		Books.remove(book);
	}
	
	public int getNumberOfBooks() {
		return Books.size();
	}

	public ArrayList<Book> getBooksByTitle(String title) {
		return Books;
	}
	
	public ArrayList<Book> remoteSort(){
		return Books;
	}
	
	public String toString(int i){
		String back;
		back = ("Title: " + Books.get(i).getTitle());
		back = back + "\nISBN: " + Integer.toString(Books.get(i).getIsbn());
		back = back + "\nRevision: " + Integer.toString(Books.get(i).getEdition());
		back = back + "\nPrice: " + Double.toString(Books.get(i).getPrice());
		back = back + "\nAuthor: \n";
		ArrayList<Author> author = Books.get(i).getAuthors();
		for(int j = 0; j < author.size(); j++){
			back = back + "\t" + author.get(j).getAuthor() + "\n";
		}
		System.out.println("*****************************************************'");
		return back;
	}
}
```

```
//Skapar skelett

package se.kth.labb3b;

import java.io.Serializable;
import java.util.ArrayList;
import java.util.Collections;

public class Book implements Comparable<Book>, Serializable {

	private String title;
	private int edition, isbn;
	private double price;
	
	private ArrayList<Author> Author = new ArrayList<Author>();

	public Book(String title, int isbn, int edition, double price, ArrayList<Author> Author) {
		this.title = title;
		this.isbn = isbn;
		this.edition = edition;
		this.price = price;
		this.Author = Author;
	}
	
	public void sortArray(Book n){
		Collections.sort(n, title);
	}

	public String getTitle() {
		return title;
	}
	
	public int getIsbn() {
		return isbn;
	}
	
	public int getEdition() {
		return edition;
	}
	
	public double getPrice() {
		return price;
	}

	public ArrayList<Author> getAuthors() {
		return Author;
	}

	public int compareTo(Book objekt) {
      if (objekt.getTitle().compareTo(this.getTitle()) < 0){
    	  return 0;
      }else{
    	  return 1;
      }
    }

	
}
```

```
package se.kth.labb3b;

import java.io.Serializable;

public class Author implements Serializable {
	private String name;

	public Author(String n){
		name = n;
	}
	
	public String getAuthor(){
		return name;
	}
}
```




Would really appreciate some help :)

---

### Post by r-senior on 2010-09-21
There are two ways of sorting in Java. One using a list of objects that implement the Comparable interface, the other using a Comparator.

When you implement the Comparable interface inside an object, you are defining what you might call the "natural order" of the object - the most common ordering of that object. A Comparator is a separate class that is dedicated to providing alternate sorting for your object.

Once a class implements the Comparable interface (by providing the compareTo() method), you can sort a list of them into their natural order by simply using:

```
Collections.sort(myListOfBooks);
```

If you choose to create a class that implements Comparator for other orderings, you would invoke that comparison using:

```
Collections.sort(myListOfBooks, myComparator);
```

Because a comparator is a separate object, you can have properties in it that switch the sort between fields with an if-then-else in the compare() method. Such a thing is commonly used in web applications that sort on columns of a table for example.

```

Comparator<Book> myComparator = new BookComparator<Book>();
...
// Sort by price
myComparator.setOrderBy("price");
Collections.sort(myListOfBooks, myComparator);

// Sort by ISBN
myComparator.setOrderBy("isbn");
Collections.sort(myListOfBooks, myComparator);

// Sort by title
Collections.sort(myListOfBooks);

```

I've typed the code off the top of my head so don't complain if it won't compile ;) but hopefully you get the idea. Seems odd at first, but does make sense.

You can simplify your compareTo() method by the way. Because String implements comparable, you can do things like this: 

```

public int compareTo(Book other) {
        return getTitle().compareTo(other.getTitle());
}

```

---

### Post by john newbuntu on 2010-09-21
It's been a while since I did java.  But since you have defined a natural ordering in Book class, you just need to call Collections.sort(books) in your remoteSort() method. You don't need a sortarray method in book class as it applies to a collection.  You could rename/refactor that remotesort() to something like sortBook().

---

### Post by emra2emra on 2010-09-21
```

package se...;

import java.util.Comparator;

public class BookComp implements Comparator {
    

    /**
     * Compares its two arguments for order, ascending.
     * Returns a negative integer, zero, or a positive integer as
     * the first argument is less than, equal
     * to, or greater than the second.<p>
     *
     * @param o1 the first object to be compared.
     * @param o2 the second object to be compared.
     * @return a negative integer, zero, or a positive integer as the
     * 	       first argument is less than, equal to, or greater than the
     *	       second.
     * @throws ClassCastException if the arguments' types prevent them from
     * 	       being compared by this Comparator.
     */
    public int compare(Object o1, Object o2) {
        String title1 = ((Book) o1).getTitle();
        String title2 = ((Book) o2).getTitle();

        if (title1 == null && title2 == null) {
            return 0;
        } else if (title1 == null) {
            return -1;
        } else if (title2 == null) {
            return 1;
        }

        return (title1.compareToIgnoreCase(title2));
    }
}

```

---

