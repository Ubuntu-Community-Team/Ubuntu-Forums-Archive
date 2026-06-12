---
title: "Java Application for a website"
date: 2013-11-15
forum: Programming Talk
---

### Post by TheodoreP on 2013-11-15
I'm creating a java application for a website and I'm still a little green and unfamiliar with java so I do have a few questions. First off, I have it hosted on github for those who want a real picture of what I my questions are asking. First question would have to be, I have a driver.java file that contains all the code for the application but I would like to move the action listeners to a separate file called listeners.java, how might I call that file into the field in the driver.java file? As well, I have been searching and searching for a good source that a beginner at java programming could use to achieve a jdbc connection to a remotely hosted database (aka my recipe database that my site uses)? Lastly, I would like to use css to format the application, but I can't find  a good tutorial for css and java anywhere?

Thank you for all your help,
Ted

P.S.

If any other question pop up I will be asking them here in this thread.

---

### Post by ofnuts on 2013-11-15
1) The standard way of oing things in Java is to have one source file per class. If you are following this convention already your application is in one single class <shudder>. Compiliing multiple files isn't complicated, you give the compiler a class path (jars and/or directories) to retrieve the classes it needs to resolve your external references.

2) See this [example]("http://www.tutorialspoint.com/jdbc/jdbc-sample-code.htm"). But your main problem is to have a proper SQL client configuration.

3) The CSS can be in static files, included by the HTML you generate. In practice for any significant development, you don't generate the HTML from Java by hand, you use something like JSP, which is more or less HTML with imbedded Java statement at strategic places to generate the variable content.

---

### Post by TheodoreP on 2013-11-15
So, if I understand you correctly, if I wanted to create a new class to hold the action listeners all's I would have to do is put a new import call at the top of the driver class and it'll work? I thank you for the link to the tutorial website. I'm still a little fuzzy on the whole css and html information you gave but I'll worry about that later. Also where in the driver class should I register the JDBC driver?

---

### Post by r-senior on 2013-11-16
All an import does in Java is allow you to use unqualified names, i.e. without specifying the package name:

```
public class Test {

    public static void main(String[] args) {
        [color="red"]java.util[/color].[color="blue"]ArrayList[/color] list = new [color="red"]java.util[/color].[color="blue"]ArrayList[/color]();
        list.add("Alpha");
        list.add("Beta");
    }
}
```

versus:

```

[color="red"]import java.util.ArrayList[/color];

public class Test {

    public static void main(String[] args) {
        [color="blue"]ArrayList[/color] list = new [color="blue"]ArrayList[/color]();
        list.add("Alpha");
        list.add("Beta");
    }
}
```

The thing that makes a piece of Java code find another piece of Java code is use of the classpath. This can be a major headache. Access to code via the classpath is required at compile time and runtime.

If you store all your source files in the same directory, as long as you don't specify the classpath through the CLASSPATH environment variable or the -cp option to javac and java, the virtual machine will find your ancilliary classes.

For example:

*~/Desktop/Test.java*
```
public class Test {

    public static void main(String[] args) {
        Person p = new Person();
        p.name = "Bob";
        System.out.println(p.name);
    }
}

```

*~/Desktop/Person.java*
```
public class Person {

    public String name;

}

```

This compiles and runs without worrying about the classpath:

```
$ cd ~/Desktop
$ javac Test.java
$ java Test
Bob

```

When you want to use code in other locations, you have to specify the classpath. If we delete the class files to clean up, then move the Person source file, for example, the compiler can't find the Person class any more, because the virtual machine is only looking in the current directory for our classes:

```
$ rm -i *.class
$ mv Person.java ~/Documents
$ javac Test.java
Test.java:4: error: cannot find symbol
        Person p = new Person();
        ^
  symbol:   class Person
  location: class Test
Test.java:4: error: cannot find symbol
        Person p = new Person();
                       ^
  symbol:   class Person
  location: class Test
2 errors

```

If we specify the classpath so that the compiler searches the Documents directory, it compiles:

```

$ javac -cp ~/Documents Test.java

```

But it doesn't run, because the Person class is not in the current directory.

```

$ java Test
Exception in thread "main" java.lang.NoClassDefFoundError: Person
	at Test.main(Test.java:4)
Caused by: java.lang.ClassNotFoundException: Person
	at java.net.URLClassLoader$1.run(URLClassLoader.java:366)
	at java.net.URLClassLoader$1.run(URLClassLoader.java:355)
	at java.security.AccessController.doPrivileged(Native Method)
	at java.net.URLClassLoader.findClass(URLClassLoader.java:354)
	at java.lang.ClassLoader.loadClass(ClassLoader.java:423)
	at sun.misc.Launcher$AppClassLoader.loadClass(Launcher.java:308)
	at java.lang.ClassLoader.loadClass(ClassLoader.java:356)
	... 1 more

```

Adding only the Documents directory to the classpath at runtime is not sufficient: The virtual machine can't find the Test class in the current directory any more because we told it only to look in Documents.

```

$ java -cp ~/Documents Test
Error: Could not find or load main class Test

```

So we have to use a classpath that includes all of the required directories (note the '.', which means current directory):

```

$ java -cp ~/Documents:. Test
Bob

```

Working with the classpath becomes even more problematic when you start putting code in packages (which you should). If you use a Java IDE, it helps with a lot of this, but you still need to grasp the concept of the classpath and its idiosyncracies.

(Note that the Person class above is not a good example in that it uses a public member variable. A real person class would have getters and setters).

---

### Post by ofnuts on 2013-11-16
Nothing really complicated in classpaths... when your class is declared as 'some.path.with.theclass', the java compiler or runtime look for 'theclass.class' in relative directory 'some/path/with/' under any directories listed in the classpath or inside any jars listed in same. In other words the "package" corresponds to a relative directory from anything listed in the classpath.

> A real person class would have getters and setters

When you use getters and setters you can never be sure that the object attributes are all coherent. For instance, with the class:

```

class Person {
 String firstName;
 String lastName;
}

```
... having setters/getters on firstName and lastName means that if you want to rename "Joe Doe" to "Jean Martin", there is point in time where that person is either "John Martin" or "Jean Doe". A true "Person" class would have constructors to set these values, and a (possibly "synchronized") "renameTo(firstName,lastName)" method to change them.

Getters and setters are an abomination, OOP- wise. No  code outside the class has any business dealing directly with attributes in a class.

Of course, in practice Java isn't used for OO programming...

---

### Post by TheodoreP on 2013-11-16
Al right, so if a class is described as private it'll only be accessible from within the file it's written in and if it's public then it'll be accessible from any file in the src or source directory. Did I get that right? I also need some help figuring out why eclipse keeps telling me that I have two errors in my code.
```

    // JDBC driver name and database URL
    static final String JDBC_DRIVER = "com.mysql.jdbc.Driver";
    static final String DB_URL = "jdbc:mysql:sara.asmallorange.com/sociable_recipes";
    // Database credentials
    static final String USER = "recipe";
    static final String PASS ="Ghost";
            
    public static void main(String[] args)
    {
        Connection conn = null;
        Statement stmt = null;
        // Register JDBC driver
        Class.forName("com.mysql.jdbc.Driver"); // eclipse says that there is an error in this line
        //Open a connection
        System.out.println("Connecting to database...");
        conn = DriverManager.getConnection(DB_URL,USER,PASS); // eclipse also tells me that this line has an error

```
For certain reasons of security right now, I have changed the password and username to different values. Once again I will state that if you'd like to get a look at the actual look of the driver.java file It is hosted on github. I however don't feel like uploading anything to github until I can figure this error out.

---

### Post by ofnuts on 2013-11-16
"private" class only applies to "inner" classes (classes declared within another class). Normal Java coding conventions require that you use a source file per class (inner class are used for menial tasks such as notification handlers). You can of course shun the conventions but the IDEs may not work as you expect if you don't.

It helps to be more explicit about the errors you get (actual message...)

1st error: likely because you are not handling the ClassNotFoundException the call can generate if the class is not found. Either use a try/catch block, or declare the whole method with a "throws ClassNotFoundExcception" but this means you will have a try/catch block around the call to your method (in other words, you just propagate the exception handling one level up)

2nd error: same thing, the call can throw an SQLException and you aren't catching it.

---

### Post by TheodoreP on 2013-11-18
Alright, you asked for the eclipse console error so here it is. If you need to see the actual file feel free to visit my github repo to check it out. I figured I would go ahead and upload it even with an error.

Exception in thread "main" java.lang.Error: Unresolved compilation problems: 
    Unhandled exception type ClassNotFoundException
    Unhandled exception type SQLException

    at driver.main(driver.java:36)

Also please let me know if I have anything in the wrong place as it sits now!

---

### Post by ofnuts on 2013-11-18
So I guessed right, you need to handle these exceptions: try/catch block or declare the method as throwing the exception (but you'll always have to handle it somewhere).

---

### Post by TheodoreP on 2013-11-18
Alright I've decided to move some of the jdbc code into the main class method and the try and catch blocks I added with the addition of a throw to SQLException. except it now returns the following error in the console

Exception in thread "main" java.lang.Error: Unresolved compilation problems: 
    Illegal modifier for parameter JDBC_DRIVER; only final is permitted
    Illegal modifier for parameter DB_URL; only final is permitted
    Illegal modifier for parameter USER; only final is permitted
    Illegal modifier for parameter PASS; only final is permitted

    at driver.main(driver.java:29)

I feel I should also mention that my web host is saying I must use the mysql connector/j to connect via jdbc.

---

### Post by r-senior on 2013-11-18
Could you post your latest code and indicate where line 29 is?

---

### Post by ofnuts on 2013-11-18
Well, you can wonder about the modifier you have next to "final" and see it is allowed inside a method definition, for instance.

---

### Post by TheodoreP on 2013-11-18
```

        // JDBC driver name and database URL
[B]        static final String JDBC_DRIVER = "com.mysql.jdbc.Driver";
        static final String DB_URL = "jdbc:mysql:sara.asmallorange.com/sociable_recipes";[/B]
        // Database credentials
[B]        static final String USER = "xxxxxxxx";
        static final String PASS ="xxxxxxxx";[/B]
        Connection conn = null;
        Statement stmt = null;

```

the four bolded lines are displayed as having errors and from top to bottom they are 29,30, 32, 33. For a better view please visit the github repo. When in eclipse I've tried telling it to remove the invalid which is the word static at the beginning of each bolded line and it results in the entire driver file failing to compile. Ok, I removed the static and final methods for the string and the errors are gone but now the driver class won't even load/compile. however the connection and statement variables are still displaying warnings for not being called in the main class method. However I do call them in the makeCentralRegion() method.

I am beginning to think that I should maybe create multiple files to display recipes from the database and call them on certain occasions in the makeCentralRegion() method. Problem is the course I took to learn java programming never went into too much detail on this subject and I'm still a bit fuzzy on the whole subject. Hell, it might even make it a little bit easier to accomplish everything I want to do by call the jdbc driver in every file that needs access to the database. Does this sound like a viable option?

---

### Post by ofnuts on 2013-11-19
Your "conn" variable is a local variable in main(). It cannot be used elsewhere. You need to make it a class attribute.

On a completely different matter, if this is for a web site IIRC your main window must be an "Applet". But you are not going to go very far with such an architecture. 

Maybe you tell us really what you want to acomplish... we don't even know what you want to use the database for.

---

### Post by r-senior on 2013-11-19
> **ofnuts said:**
> Maybe you tell us really what you want to acomplish... we don't even know what you want to use the database for.
I am also unclear. I've seen the website and seen your program and can't really see where they fit together. If you want to write an application where people can submit recipes, you are better off writing a web application. Perhaps this Swing application is just a tool for you to load data into the database, or perhaps it's just for the hell of it? Either is OK but there's no point you putting loads of work into it in the belief that the masses will use it to create recipes in your database.

Going back to your JDBC issues, the usual approach is to use a data access object (DAO) pattern, i.e. you make a separate class that has all the JDBC anguish in it. Then you expose nice methods like findAllRecipes, createRecipe, etc.

I did get your code compiled, although I didn't go much further.

A few points:

1. When you are working with a JDBC driver, you only need to load the class into the JVM, you don't need to create an instance of it

```

    try {
        Class.forName("com.mysql.jdbc.Driver");
    }
    catch (ClassNotFoundException e) {
        // Handle your exception here
    }

```

This relieves you of a couple of exception handlers for IllegalAccessException and InstantiationException.

2. Your database URL should be 

```
String DB_URL = "jdbc:mysql://sara.asmallorange.com/sociable_recipes";
```

[https://dev.mysql.com/doc/refman/5.0/en/connector-j-reference-configuration-properties.html](https://dev.mysql.com/doc/refman/5.0/en/connector-j-reference-configuration-properties.html)

3. You need to get your JDBC driver JAR into the classpath. See discussion above regarding classpath.

4. The rest of it was just adding throws clauses and moving that conn variable around, as Ofnuts suggested. IMO you should go for the DAO idea sooner rather than later because this class is going to be unmanageable with all that JDBC code in it.

5. Java classes usually start with an uppercase character, i.e. Driver rather than driver. Beware of confusion with the JDBC driver.

---

### Post by TheodoreP on 2013-11-19
I'm working on this application partly for the hell of it and partly to learn a new language. However I am hoping to eventually create a stand alone application to allow users to view, print, edit, create new recipes and comment on other people's recipes all outside of a web browser. Also I don't really understand the whole web app thing or how to create web apps? To me if you want to create a web app I think why not create a whole application, but I could be wrong. Although my website is coded fully in php and css! Ya, I know it doesn't have javascript and that is probably what makes a website into a web app but I am working on trying to add a little javascript into the project. However all this is just a hobby for me. Brings up an interesting question though, are AJAX and JavaScript the same? When talking about this DOA idea are you saying that I should move all the jdbc connection info over to a new and seperate file so as to make my code more manageable? Kinda of an off question but is it possible to create a gui application with perl?

---

### Post by r-senior on 2013-11-19
A web app is just an application whose user interface is a web browser. A lot of the HTML will be generated dynamically, often from a database. Isn't that what you have done with PHP?

You've got the DAO idea -- move all the ugly JDBC code into its own class so that you don't have to look at it. Something along these lines:

```
public class RecipeDAO {

	private Connection connection;

	public RecipeDAO(Connection connection) {
		this.connection = connection;
	}

	public List<Recipe> findAllRecipes() throws SQLException {
		Statement statement = null;
		ResultSet resultset = null;
		try {
			List<Recipe> recipes = new ArrayList<>();
			statement = connection.createStatement();
			resultset = statement.executeQuery("select * from recipes");
			while (resultset.next()) {
				Recipe recipe = new Recipe();
				// Populate the properties of the recipe here
				// ...
				
				// Add it to the list of recipes
				recipes.add(recipe);
			}
			return recipes;
		}
		finally {
			// Close statement and resultset here (more try/catch required, unfortunately)
			// ...
		}
	}
	
	// More methods here, createRecipe, updateRecipe, findRecipeByIngredient, etc, etc.

}
```

A DAO connoisseur, i.e. someone who can't face writing yet another one, would write a template class for the repetitive JDBC code, or use an existing one like [Spring's JdbcTemplate]("http://docs.spring.io/spring/docs/3.2.4.RELEASE/spring-framework-reference/html/jdbc.html#jdbc-JdbcTemplate").

---

### Post by TheodoreP on 2013-11-19
so for the jdbc dao file assuming I use the same concept you have here, it would probably look a lot like this:
```

public class RecipeDAO {
    // JDBC driver name and database URL
    String DB_URL = "jdbc:mysql://sara.asmallorange.com/sociable_recipes";
    // Database credentials
    String USER = "xxxxxxxxx";
    String PASS ="xxxxxxxxx";
    Connection conn = null;
    Statement stmt = null;
    // Register JDBC driver
       try {
           Class.forName("com.mysql.jdbc.Driver");
       }
       catch (ClassNotFoundException e) {
           // Handle your exception here
       }
        //Open a connection
        System.out.println("Connecting to database...");
        conn = DriverManager.getConnection(DB_URL,USER,PASS);
}

```

However, that leads to the question of how the application knows to grab the connection information and weather or not I should import the java.sql.* packages in to the newly renamed power file or the doa file? As well, should each jdbc function be called in the RecipeDAO file or should they each have their own files? Sorry, if I'm overwhelming  you with questions but the courses I took for java were online and I have to say that I'm learning more from you in my free time than when I actually paid to learn this language. At least more real world knowledge. As far as I'm concerned.

---

### Post by r-senior on 2013-11-20
In my mind, it doesn't look quite like that.

Opening a connection is a relatively expensive operation. In a desktop application like this, you probably want to open the connection when the application starts and keep it open until it exits. It's not going to completely kill the application if you open and close connections in each DAO method but it makes more sense to have the main program open the connection and then pass it to DAOs that need it. Hence the constructor in my example that takes a connection as a parameter.

Also, looking ahead a little, sharing the connection between DAOs allows you to work with transactions if you need to. You can start a transaction, have one DAO write to one table, another DAO write to another table, then commit or rollback the two operations as one transaction.

So I think, initially at least, your main class will have some startup code that opens the database connection and constructs each DAO that you need:

```

public class Driver {

    private Connection connection
    private RecipeDAO recipeDAO;
    private IngredientDAO ingredientDAO;

    // Call this when the appication is on screen and wants to connect
    private void init() throws SomeExceptions {
        this.connection = DriverManager.getConnection(...);
        this.recipeDAO = new RecipeDAO(this.connection);
        this.ingredientDAO = new IngredientDAO(this.connection)
        ...
    }

    // Call this when the application quits
    private void cleanup() throws SomeExceptions {
        this.connection.close();
    }

    // Working with the database is nice and clean because we use the DAO
    private void someActionHandler() {
        List<Recipe> recipes = this.recipeDAO.findAllRecipes();
        ...
    }
...

```

I'd use a separate init method rather than the constructor because I'd want to get the main application window on screen before attempting a connection to the database. Then you can pop up some sort of "connecting" dialog while you connect and report any errors gracefully.

Swing applications are not really my thing and people who have written more of them might have better ideas but that's the approach I would start off with. The key point, I think, is that the connection should not be opened and closed by the DAO. It needs a wider scope.

---

### Post by ofnuts on 2013-11-20
> **MasterProgram said:**
> so for the jdbc dao file assuming I use the same concept you have here, it would probably look a lot like this:
```

public class RecipeDAO {
    // JDBC driver name and database URL
    String DB_URL = "jdbc:mysql://sara.asmallorange.com/sociable_recipes";
    // Database credentials
    String USER = "xxxxxxxxx";
    String PASS ="xxxxxxxxx";
    Connection conn = null;
    Statement stmt = null;
    // Register JDBC driver
       try {
           Class.forName("com.mysql.jdbc.Driver");
       }
       catch (ClassNotFoundException e) {
           // Handle your exception here
       }
        //Open a connection
        System.out.println("Connecting to database...");
        conn = DriverManager.getConnection(DB_URL,USER,PASS);
}

```
No, because the code isn't in a method (not even in the instance initializer)

> **MasterProgram said:**
> However, that leads to the question of how the application knows to grab the connection information
You use a dedicated class for the connection using a [singleton pattern with lazy initialization]("http://en.wikipedia.org/wiki/Singleton_pattern").

> **MasterProgram said:**
> and weather or not I should import the java.sql.* packages in to the newly renamed power file or the doa file? 
You put the imports in all the classes that directly reference them.

> **MasterProgram said:**
> As well, should each jdbc function be called in the RecipeDAO file or should they each have their own files?

You have to understand the difference between the "file" and the "class". The "class" is a programming concept, the file is a way to store bytes. The Java convention is to use a source file per class. So your real question is how do you split your code in classes... You can start to work with the black box principle. A class is a black box for the rest of the code: the outside is nice and shiny (methods) the inside is hopefully clean too, but sometimes not so, and anyway the rest of the code doesn't care and shouldn't care. You can change the class contents without having to change anything outside. Do the DAO classes need to know how you create the DB connection? Not really, they just want one, so here is your DB connection class. Does the Recipe class need to know how the data is setup in the DB? Not really, so here is your RecipeDAO class. This is also true of the UI, parts of the UI can be classes of their own (main panel (often a JPanel) and all the stuff below (buttons, entry fields...)). Speaking of the UI, the usual practice is to use the [MVC architecture]("http://en.wikipedia.org/wiki/Model-view-controller") where Model, View, and Controller are usually three different classes.

---

### Post by TheodoreP on 2013-11-25
Ok, sorry for the delay on this post. I needed to take a break from the application creation process. Now however I find myself wondering what books both hardcover and google play books you recommend for learning JDBC programming? I find it a little tedious and unnecessary having to come back and post new questions.

---

### Post by ofnuts on 2013-11-26
You don't need a book for JDBC, [this tutorial]("http://docs.oracle.com/javase/tutorial/jdbc/basics/") is plenty enough for most people. But that assumes you know some SQL...

---

### Post by r-senior on 2013-11-26
I had a quick look at the books available from a couple of well known online book sellers and I have to say: Beware - look at the dates! I can't believe they are selling Java books that were published 5-10 years ago -- Tomcat 4, Spring 2 and "Java 6 Platform Revealed". Revealed? It's been and gone and isn't even supported any more!

Most of the JDBC books I looked at were out of date compared to the tutorial that ofnuts linked.

---

### Post by TheodoreP on 2013-11-26
Alright and just so I'm clear I want a connection dao file not just an object in the power/driver file?

---

### Post by r-senior on 2013-11-26
That's not clear to me, but if it's clear to you, all is well. :)

---

### Post by TheodoreP on 2013-11-26
When using the datasource object method, the way I'm understanding the tutorial I need to purchase a driver and server from another company or am I misunderstanding something? Also, just to cover my bases, Using datasource objects is compatable with the mysql connector/J correct? And another question, it appears that the javax.ejb library isn't on my computer where might I find it? I've got the openjdk 7 runtime on my machine running ubuntu 13.10 though.

Now just to make sure I understand the basics the connection file would look similar to this minus the credentials, correct?

```

import java.sql.*;
import javax.sql.*;
import javax.ejb.*;
import javax.naming.*;
public class Connection implements SessionBean{
    // ...
    ctx = new InitialContext();
    ds = (DataSource)ctx.lookup("jdbc:mysql://sara.asmallorange.com/sociable_recipe");
    Connection con = ds.getConnection(xxxxxx, xxxxxx);
    try {
        Connection con = ds.getConnection(xxxxxx, xxxxxx);
        // ... code to use the pooled
        // connection con
    } catch (Exception ex {
        // ... code to handle exceptions
    } finally {
        if (con != null) con.close();
    }
    public void ejbCreate() throws CreateException {
        ctx = new InitailContext();
        ds = (DataSource)ctx.lookup("jdbc:mysql://sara.asmallorange.com/sociable_recipe");
    }
    
}

```

---

### Post by r-senior on 2013-11-26
You don't need a DataSource for the scale of application you are writing. You can just get your connection from the DriverManager, as you have been doing.

The tutorial uses the term "vendor" but that doesn't mean you need to buy anything. They just use that term to refer to the organisation that creates the database and drivers.

DataSources can be used with the MySQL driver but you don't need DataSources. These are more useful in large scale enterprise applications and Java web applications. It's all about central administration and shared connection pools. Which you don't need.

You can do your connections like this, which is what you are doing already.

[http://docs.oracle.com/javase/tutorial/jdbc/basics/connecting.html](http://docs.oracle.com/javase/tutorial/jdbc/basics/connecting.html)

IMO, the thing to concentrate on is moving your JDBC code into another class and getting it working with your main program.

Edit: The code you added is EJB code. You don't need that complexity for a single user app.

---

### Post by TheodoreP on 2013-11-26
Alright, thanks for clarifying for me. I think I will be switch to the DriverManager method then perhaps. When you say single user app, you mean a non-network app right? As in a computer app for use by several people but not on the same network connection.

Ok, using the DriverManager class instead the connection DAO file should look similar to this correct:

```

import java.sql.Connection;
import java.sql.DriverManager;
import java.sql.SQLException;

public class Connection getConnection() throws SQLException{
    Connection conn = null;
    Properties connectionProps = new Properties();
    connectionProps.put("xxxxxx", this.userName);
    connectionProps.put("xxxxxx", this.password);
        
    if(this.dbms.equals("mysql")) {
        conn = DriverManager.getConnection("jdbc:" + this.dbms + 
                "://sara.asmallorange.com:xxxx/sociable_recipe",
                connectionProps);
    } else if(this.dbms.equals("derby")) {
        conn = DriverManager.getConnection("jdbc:" + this.dbms + 
                "://sara.asmallorange.com:xxxx/sociable_recipe",
                connectionProps);
    }
    System.out.println("Connected to database");
    return conn;
}

```

---

### Post by r-senior on 2013-11-26
Single user application in the sense of one user using each instance of the application.

OK, so you have made a step forward in the sense that you have moved your "connect to the database" code into a separate class. I think you still have some compilation issues to sort out:

```
public class Connection getConnection() throws SQLException{
```

That's not quite right.

Compilation issues aside, you've written a little connection factory -- a class that gives you connections. Do you think Connection is a good name for your class, or might you confuse it with java.sql.Connection?

If you call the getConnection method twice from your driver class, will you get the same connection or a different connection? Which way would be better for your application? Same each time, or different each time?

Will your connection factory class close the connection or connections when you are done? Or will the driver class handle that?

---

### Post by TheodoreP on 2013-11-26
Ok, I changed the name of the connection file to ConnectionDAO. However eclipse is still telling me that I have a syntax error on lines 6 and 23 and smaller errors on lines 9, 10, 12, 13, 16, 17.

```

import java.sql.Connection;
import java.sql.DriverManager;
import java.sql.SQLException;
import java.util.Properties;

public class ConnectionDAO Connection getConnection() throws SQLException{
    Connection conn = null;
    Properties connectionProps = new Properties();
    connectionProps.put("xxxxxx", this.userName);
    connectionProps.put("xxxxxx", this.password);
        
    if(this.dbms.equals("mysql")) {
        conn = DriverManager.getConnection("jdbc:" + this.dbms + 
                "://sara.asmallorange.com:xxxx/sociable_recipe",
                connectionProps);
    } else if(this.dbms.equals("derby")) {
        conn = DriverManager.getConnection("jdbc:" + this.dbms + 
                "://sara.asmallorange.com:xxxx/sociable_recipe",
                connectionProps);
    }
    System.out.println("Connected to database");
    return conn;
}

```

---

### Post by r-senior on 2013-11-27
I think you may misunderstand the concept of a data access object (DAO).

[https://en.wikipedia.org/wiki/Data_access_object](https://en.wikipedia.org/wiki/Data_access_object)
[http://www.oracle.com/technetwork/java/dataaccessobject-138824.html](http://www.oracle.com/technetwork/java/dataaccessobject-138824.html)

A recipe DAO will find recipes, create recipes, delete recipes and so on. The class you have creates connections so is more of a connection factory than a data access object. 

I don't think you have the pieces set out in your mind and how they will fit together. You need to work on that.

Your compilation errors are because:

a. You are mixing a class definition with a method definition. You should have something more like:

```
public class ConnectionFactory {

	public Connection getConnection() throws SQLException {
            ...

```

b. You are referring to members of the class that don't exist: userName, password and dbms

But ... rather than just putting your head down and coding, you need to have a clear picture of how your main components fit together. That was the original question: how to split your application up into manageable components ... but I don't think you have the answer in your head.

Looking back at the thread, the main components appear to be:

1. Your main program
2. Something that manages connections (ConnectionFactory?)
3. Something that manages recipes (RecipeDAO?)

As an exercise, you could consider writing Hello World using two collaborating classes:

*Hello.java*
```

public class Hello {

    ...

}

```

*MessageProvider.java*
```

public class MessageProvider {

    public String getMessage() {
        return "Hello World";
    }

}

```

If you can do that and understand it, it's a step forward to reorganising your real application.

---

### Post by TheodoreP on 2013-11-28
Yes, I realize that I probably need to think my application through a little more clearly, but the thing is that I program to relieve stress and mellow out. After a long hard day of work, and little before work, I need to relax and this is one way of coping. Especially since I feel like and my parents agree that my employer is seriously screwing me out of every possible promotion that is opening up. Three times now I've been passed over. Enough of the ranting though, How might I call the getConnection() method from the ConnectionFactory file in the power file? I'm I correct in assuming that it might look somewhat like this:
```

connectionfactory.getConnection();

```
I'm currently calling the dao and connectionfactory files with the following code:
```

    // call to the database ConnectionFactory
    private ConnectionFactory connectionfactory;
    // call to the database access objects
    private RecipeDAO recipeDAO;
    private CommentsDAO commentsDAO;
    private UsersDAO usersDAO;

```

---

### Post by r-senior on 2013-11-28
When you program for pleasure, you have the freedom to create a piece of programming art that you can admire and be proud of.

This is looking good (it's so good, you don't even need the comments):

> 
```
connectionfactory.getConnection();
```

```

    // call to the database ConnectionFactory
    private ConnectionFactory connectionfactory;
    // call to the database access objects
    private RecipeDAO recipeDAO;
    private CommentsDAO commentsDAO;
    private UsersDAO usersDAO;
```


---

### Post by TheodoreP on 2013-11-29
Need some help with my viewallrecipes method, I'm trying to create a way to display a list of all the recipes within the database so that I can ensure my connecionfactory is truly working it's wonderful magic and I'm having a little trouble calling the method in the power file as well as the printsqlexception at the end of the viewallrecipes method in the recipesdao file, However that can wait a little bit right now.

the following is the code used to call the viewallrecipes method in the power file
```

    private void makeCentralRegion() throws SQLException
    {
        Connection con = null;
        recipeDAO.viewAllRecipes(con, "sociable_recipe");
    }

```

and here is the viewallrecipes method code
```

    public void viewAllRecipes(Connection con, String dbname) throws SQLException {
        Statement stmt = null;
        String query = "select recipeid, title, poster, shortdesc from recipes";
        try {
            stmt = con.createStatement();
            ResultSet rs = stmt.executeQuery(query);
            while(rs.next()) {
                int recipeid = rs.getInt("recipeid");
                String title = rs.getString("title");
                String poster = rs.getString("poster");
                String shortdesc = rs.getString("shortdesc");
                System.out.println(recipeid + "/t" + title + "/t" + "posted by: Chef" + poster + "/t" + shortdesc);
            }
        } catch(SQLException e){
            power.printSQLException(e);
        } finally {
            if(stmt != null) { stmt.close(); }
        }
    }

```

My main issue is that I can't seem to understand how and what arguments to place in the parentheses.

---

### Post by r-senior on 2013-11-29
I wasn't sure which parentheses you meant.

At this stage, your DAO should look more like:

```
public class RecipeDAO {

    private Connection connection;

    public RecipeDAO(Connection connection) {
        this.connection = connection;
    }

    public List<Recipe> findAllRecipes() throws SQLException {
        Statement s = null;
        List<Recipe> recipes = new ArrayList<Recipe>();
        try {
            s = this.connection.createStatement();
            ...
            // Run your query, iterate over the results and add recipes to the list
            ...
            return recipes;
        }
        finally {
            // Close statement and resultset (but not the connection)
            ...
        }
    }

}

```

You don't want to catch the exception because you aren't doing anything useful with it. For now, let's just declare that you throw it and let your main program deal with it.

In your main program, you'll get your connection from your connection factory and create the DAO:

```

private void connectToDatabase() throws SQLException {
    ConnectionFactory factory = new ConnectionFactory();
    this.connection = connectionFactory.getConnection();
    this.recipeDAO = new RecipeDAO(connection);
    ...
}
```

When you want a list of recipes, you call the DAO:

```
List<Recipe> recipes = recipeDAO.findAllRecipes();
for (Recipe recipe : recipes) {
    // Do something with each recipe, e.g. add to the model for a Swing table
}
```

I'm assuming you understand the basics of using generics (the things in the <> brackets). If not, please say so.

---

### Post by TheodoreP on 2013-11-29
> I'm assuming you understand the basics of using generics (the things in the <> brackets). If not, please say so.
I never really learned about these generics your talking about in the online courses I took, so I must answer no to your assumption. Could you please give a good example of how to code a query and iterate it over and over until all the recipes in the database are displayed. I have column named recipeid that auto-increments with every new recipe. As well, I was wondering if you could give a good example of how too close a statement and a resultset? In the recipe dao file everything is looking good but eclipse is showing me that lines 12 and 14 have errors in them and the errors are the <Recipe> generics? It could be that I just haven't added my iterated query and resultset yet but I don't know.

---

### Post by 1clue on 2013-11-29
Never mind, replied to something on the first page which no longer is pertinent.

---

### Post by ofnuts on 2013-11-30
> **MasterProgram said:**
> Could you please give a good example of how to code a query and iterate it over and over until all the recipes in the database are displayed. 

This is normally something you avoid. Whats is costly in DB interaction is the request. Unless you are handling tens of megabytes of data or making very complex queries, you get much better performance by getting all your data in one query.

---

### Post by r-senior on 2013-11-30
> **MasterProgram said:**
> I never really learned about these generics your talking about in the online courses I took, so I must answer no to your assumption. 

Generics do many things, but of relevance here is that the finder methods, e.g. findAllRecipes return a list of recipes, which is defined as a return type of List<Recipe>. The generic part defines the type of object in the list. This makes it easy to iterate over:

*Main Program*
```
List<Recipe> recipes = recipeDAO.findAllRecipes();
for (Recipe recipe : recipes) {
   // Do something with each recipe
}
```

> Could you please give a good example of how to code a query and iterate it over and over until all the recipes in the database are displayed.
If I did that, I'd have written the whole method. So I'll let you do that part.

> I have column named recipeid that auto-increments with every new recipe.
You can define your primary key column as auto-increment. When you insert a recipe, don't set the primary key and the database will handle it.

[https://dev.mysql.com/doc/refman/5.5/en/example-auto-increment.html](https://dev.mysql.com/doc/refman/5.5/en/example-auto-increment.html)

[quote=OfNuts]This is normally something you avoid. Whats is costly in DB interaction is the request. Unless you are handling tens of megabytes of data or making very complex queries, you get much better performance by getting all your data in one query.[/quote]
That's the way I read it. Then I read it a few more times and started to hope that it meant, "how to code a query and iterate over it".

---

### Post by TheodoreP on 2013-11-30
So, just to get a little hint of how to code the query and iterate it over and over until all recipes in the database are displayed I'll post some code and you can tell me if I'm close.
```

import java.sql.Connection;
import java.sql.ResultSet;
import java.sql.SQLException;
import java.sql.Statement;
import java.util.*;

public class RecipeDAO {
    private Connection connection;
    public RecipeDAO(Connection connection) {
        this.connection = connection;
    }
    public List<**Recipe**> findAllRecipes() throws SQLException {
        Statement s = null;
        List<**Recipe**> recipes = new ArrayList<**Recipe**>();
        s = this.connection.createStatement();
        // Run your query, iterate over the results and add recipes to the list
        String query = "select recipeid, title, poster, shortdesc from recipes";
        try {
            ResultSet rs = s.executeQuery(query);
            while(rs.next()) {
                int recipeid = rs.getInt("recipeid");
                String title = rs.getString("title");
                String poster = rs.getString("poster");
                String shortdesc = rs.getString("shortdesc");
                System.out.println(recipeid + "/t" + title + "/t" + "posted by: Chef" + poster + "/t" + shortdesc);
            }
            return recipes;        
        } finally {
            // Close statement and resultset (but not the connection)
                    if(s != null) { s.close(); }
        }
    }
}

```

So tell me, if I'm understanding how to query a database and iterate it over? If so, why is it telling me that the bolded generics are wrong or errors? As well, please let me know if I closed out the statement and resultset but, not the connection correctly?

As well in my power file in these lines:
```

    private void connectToDatabase() throws SQLException {
        ConnectionFactory factory = new ConnectionFactory();
        this.connection = **ConnectionFactory.getConnection();**
        this.recipeDAO = new RecipeDAO(connection);
    }

```
The bolded lines are recommending that I go to the getConnection() method and add a static type before the Connection type. Well, I tried it but I undid it because it then gives a whole bunch of errors in the getConnection() method and that means that it's wrong because keeping it how I have it now gives zero errors. Please help me with this if you could?

---

### Post by r-senior on 2013-11-30
It's close, but

a. You aren't adding a Recipe object to the list of recipes. This could be because you don't have one, and that would explain the errors on the generics. They expect you to have a Recipe object.

b. In the finally, you've closed the statement but not the result set. You'll need to move the declaration of the resultset up to the same place you declared the statement, otherwise you won't be able to reference it in the finally block.

Very close though.

---

### Post by TheodoreP on 2013-11-30
Alright I got the statement and resultset closed I do believe. The following is the new dao script.
```

import java.sql.*;
import java.util.*;

public class RecipeDAO {
    private Connection connection;
    public RecipeDAO(Connection connection) {
        this.connection = connection;
    }
    public List<Recipe> findAllRecipes() throws SQLException {
        Statement s = null;
        ResultSet rs = null;
        List<Recipe> recipes = new ArrayList<Recipe>();
        s = this.connection.createStatement();
        // Run your query, iterate over the results and add recipes to the list
        String query = "select recipeid, title, poster, shortdesc from recipes";
        try {
            rs = s.executeQuery(query);
            while(rs.next()) {
                int recipeid = rs.getInt("recipeid");
                String title = rs.getString("title");
                String poster = rs.getString("poster");
                String shortdesc = rs.getString("shortdesc");
                System.out.println(recipeid + "/t" + title + "/t" + "posted by: Chef" + poster + "/t" + shortdesc);
            }
            return recipes;        
        } finally {
            // Close statement and resultset (but not the connection)
            if(s != null) { s.close(); }
            if(rs != null) { rs.close(); }
        }
    }
}

```

---

### Post by r-senior on 2013-11-30
Good. You just need to build a Recipe object in the while loop and add it to the list and I think you have got it. At the moment, your list of recipes will always be empty.

---

### Post by TheodoreP on 2013-11-30
I've been trying to figure this and just can't figure out a way of declaring an arraylist object, could you give me a link to a good tutorial?

Ok, I don't think I got this right but I figured I'd check and post it anyways:
```

import java.sql.*;
import java.util.*;

public class RecipeDAO {
    private Connection connection;
    private List<Recipe> recipe;

    public RecipeDAO(Connection connection) {
        this.connection = connection;
    }
    public List<Recipe> findAllRecipes() throws SQLException {
        Statement s = null;
        ResultSet rs = null;
        List<Recipe> recipes = new ArrayList<Recipe>();
        s = this.connection.createStatement();
        // Run your query, iterate over the results and add recipes to the list
        String query = "select recipeid, title, poster, shortdesc from recipes";
        try {
            rs = s.executeQuery(query);
            while(rs.next()) {
                int recipeid = rs.getInt("recipeid");
                String title = rs.getString("title");
                String poster = rs.getString("poster");
                String shortdesc = rs.getString("shortdesc");
                recipes.add(rs.getString(recipeid));
                recipes = (String[]) recipes.toArray(new String[recipes.size]);
            }
            return recipes;        
        } finally {
            // Close statement and resultset (but not the connection)
            if(s != null) { s.close(); }
            if(rs != null) { rs.close(); }
        }
    }
}

```

---

### Post by r-senior on 2013-12-01
It's simpler than you are making it. You already have the list of recipes (blue). Just make a recipe object and add it to the list of recipes (red).

```
import java.sql.*;
import java.util.*;

public class RecipeDAO {
    private Connection connection;
    private List<Recipe> recipe;

    public RecipeDAO(Connection connection) {
        this.connection = connection;
    }
    public List<Recipe> findAllRecipes() throws SQLException {
        Statement s = null;
        ResultSet rs = null;
        [color="blue"]List<Recipe> recipes = new ArrayList<Recipe>();[/color]
        s = this.connection.createStatement();
        // Run your query, iterate over the results and add recipes to the list
        String query = "select recipeid, title, poster, shortdesc from recipes";
        try {
            rs = s.executeQuery(query);
            [color="red"]Recipe recipe = new Recipe();[/color]
            while(rs.next()) {
                [color="red"]recipe.setRecipeId(rs.getInt("recipeid"));[/color]
                [color="red"]recipe.setTitle(rs.getString("title"));[/color]
                [color="red"]recipe.setPoster("poster"));[/color]
                [color="red"]recipe.setShortDesc(rs.getString("shortdesc"));[/color]
                recipes.add([color="red"]recipe[/color]);
            }
            return recipes;        
        } finally {
            // Close statement and resultset (but not the connection)
            if(s != null) { s.close(); }
            if(rs != null) { rs.close(); }
        }
    }
}
```

You'll need a recipe object, but that's just a simple Java bean.

---

### Post by TheodoreP on 2013-12-01
Alright I changed the code to look more like yours but, eclipse still says that the bolded words are causing problems? I think that is what is causing me to over think things.

```

import java.sql.*;
import java.util.*;

public class RecipeDAO {
    private Connection connection;

    public RecipeDAO(Connection connection) {
        this.connection = connection;
    }
    public List<**Recipe**> findAllRecipes() throws SQLException {
        Statement s = null;
        ResultSet rs = null;
        List<**Recipe**> recipes = new ArrayList<Recipe>();
        s = this.connection.createStatement();
        // Run your query, iterate over the results and add recipes to the list
        String query = "select recipeid, title, poster, shortdesc from recipes";
        try {
            rs = s.executeQuery(query);
            **Recipe** recipe = new **Recipe**();
            while(rs.next()) {
                recipe.setRecipeId(rs.getInt("recipeid"));
                recipe.setTitle(rs.getString("title"));
                recipe.setPoster(rs.getString("poster"));
                recipe.setShortDesc(rs.getString("shortdesc"));
                recipes.add(recipe);
            }
            return recipes;        
        } finally {
            // Close statement and resultset (but not the connection)
            if(s != null) { s.close(); }
            if(rs != null) { rs.close(); }
        }
    }
}

```

The eclipse console displays the following error:

> [COLOR=#ff0000]Exception in thread "main" java.lang.Error: Unresolved compilation problems: 
    The type List is ambiguous
    Recipe cannot be resolved to a type
    The method findAllRecipes() from the type RecipeDAO refers to the missing type Recipe
    Recipe cannot be resolved to a type[/COLOR]

---

### Post by r-senior on 2013-12-01
You need a Recipe class.

---

### Post by TheodoreP on 2013-12-01
So after creating the recipe class I then need to create the set methods correct?

---

### Post by r-senior on 2013-12-01
Yes, then re-read OfNuts' comments about getters and setters early in the thread.

---

### Post by TheodoreP on 2013-12-02
So, after creating the recipe class and making the set methods, do I need to use sql code to query the database?

---

### Post by r-senior on 2013-12-03
You will use the DAO to query the database:

*Main Program*
```
List<Recipe> recipes = recipeDAO.findAllRecipes();
```

---

### Post by TheodoreP on 2013-12-04
Does the recipe dao file already have the getters created or along with creating the setters in the recipe file do I need to create the getters?

---

### Post by r-senior on 2013-12-04
Your DAO does not need getters and setters.

Getters and setters are not created automatically in Java, but the major IDEs (Eclipse, Netbeans, IDEA) have menu options to generate them.

---

### Post by TheodoreP on 2013-12-05
ok, the actual question was about whether or not I needed to create getters and setters in the recipe.java file or just the setters?

---

### Post by r-senior on 2013-12-05
Your Recipe class will need getters so that you can access properties of your recipe in your main program after you have fetched lists of recipes with your Recipe DAO.

---

### Post by TheodoreP on 2013-12-08
Could I get you to give me an example of what the getters and setters might look like?

---

