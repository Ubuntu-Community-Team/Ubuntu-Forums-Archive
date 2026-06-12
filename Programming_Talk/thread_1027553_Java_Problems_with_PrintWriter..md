---
title: "Java: Problems with PrintWriter."
date: 2009-01-01
forum: Programming Talk
---

### Post by StephanG on 2009-01-01
Hey guys.  I'm trying to write a small application that will store a list of people's user names and passwords on a .txt file.  The idea is simple: Create a User class.  And store the User in an ArrayList.  I'm also creating a method that will allow me to read the .txt file and add the users to the ArrayList at the beginning.  After that the users should be automatically added to "UserList.txt".  My User class looks as follows:

import java.io.FileNotFoundException;
import java.io.PrintWriter;

public class User 
{
	public User(String n, String p) throws FileNotFoundException
	{
		name = n;
		password = p;
		
		PrintWriter out = new PrintWriter("UserList.txt");
		out.println(name);
		out.println(password);
	}
	
	public String getName()
	{
		return name;
	}
	
	public String getPassword()
	{
		return password;
	}
	String name;
	String password;
}


I know, I'm being a bit lazy with the exception.  But I first want to get the writer to work.

My next class that contains the main method looks like this:

import java.util.ArrayList;
import java.util.Scanner;
import java.io.FileNotFoundException;
import java.io.FileReader;

public class Lock 
{
	public void createUser(String n, String p) throws FileNotFoundException
	{
		User temp = new User(n,p);
		userList.add(temp);
	}
	public void readUserList() throws FileNotFoundException
	{
		FileReader reader = new FileReader("UserList.txt");
		Scanner in = new Scanner(reader);
		
		while (in.hasNextLine())
		{
		String name = in.nextLine();
		String password = in.nextLine();
		User temp = new User(name, password);
		userList.add(temp);
		}
	}
	
	public void writeUserList()
	{
		for(int i=0; i<userList.size(); i++)
		{
			String n = userList.get(i).getName();
			String p = userList.get(i).getPassword();
			System.out.println(n + "   " + p);
		}
	}
	public static void main(String[] args) throws FileNotFoundException 
	{
		Lock padlock = new Lock();
		User me = new User("John", "JohnPassWord");
	}
	ArrayList<User> userList = new ArrayList<User>();
}

Essentially everything I will be doing will be a method of the lock class.  This includes a wrapper method for creating Users as well as adding them to the ArrayList.  The problem is that upon running: 

User me = new User("John", "JohnPassWord");

The .txt file is completely wiped of all its contents.  Why is this happening?  Shouldn't it only add to the text?

Thanks for any help in advance.

---

### Post by StephanG on 2009-01-01
Wow its hard to read without indentations.

---

### Post by mike_g on 2009-01-01
You can use a [filewriter](http://java.sun.com/j2se/1.4.2/docs/api/java/io/FileWriter.html) with the append bit set. 
 
also if you use code tags your code will keep its indentation. eg:
[ code ] [ /code ] without the spaces.

---

### Post by StephanG on 2009-01-01
You mean move the writer to the createUser method.  Okay...  mmm... It still doesn't work.  Will try with filewriter and let you know.

---

### Post by StephanG on 2009-01-02
Okay, thanks for the help, but I bypased hte problem.  I no longer need to write to the file.  Thanks anyway.

---

