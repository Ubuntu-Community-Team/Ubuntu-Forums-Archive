---
title: "DB Queries in Java Program"
date: 2012-12-16
forum: Programming Talk
---

### Post by kevinharper on 2012-12-16
During the past few weeks I have been asking a bunch of questions for my final project for a Java class I was taking (ended Thursday).

The program had enough to get a descent grade but is nowhere near a level that can be considered for production. The code is messy and inefficient. Needless to say, I would like to redo it for my own personal knowledge.

My first question is about queries to a MySQL database. Is it best to have a single MyDBQueries class or is it better to include the queries within the class that needs the results?

---

### Post by Some Penguin on 2012-12-16
Usually I prefer to separate storage logic from application logic -- only the internals of the storage layer need to be aware of the exact data store and its uses.  The storage API provides basic operations -- querying, insertions, updates, deletions -- without explicitly indicating how (e.g. it doesn't use any SQL-specific classes).

That way, application code is significantly less fragile and doesn't need to be aware of potentially thorny details (like, say,  how a complex data structure within the basic Java-side object might be mapped to a single column in a database row; maybe it's serialized as JSON, but the client shouldn't have to care).

It also means that it's easier to use a non-SQL implementation -- like a straightforward version that has an ephemeral store that puts everything on the JVM heap (for unit-testing applications which are merely consumers of the storage system, for instance; or for rapidly iterating and testing application logic before you finalize a schema, or use a service-oriented architecture where clients access the storage layer over e.g. HTTP.

---

### Post by kevinharper on 2012-12-16
Okay.

So the way I have
```
String result = Class.getResultFromQueryMethod()
```
in the class that uses the query result, where Class is the class that holds all the different queries, each query within its own accessor method. Kosher? That is pretty much what you suggested, right?

---

### Post by trent.josephsen on 2012-12-16
Only if the data you *really want* is actually the String that method returns.

[Data access object](http://en.wikipedia.org/wiki/Data_access_object)

[Object/relational mapping](http://en.wikipedia.org/wiki/Object-relational_mapping)

The idea is not simply to consolidate queries into a class by themselves, but to encapsulate access to the database so that the actual database used is irrelevant to the client code. So your intermediary class / DAO / whatever you call it should do the translation between the format your database uses and the objects used in the rest of your Java code. E.g. if your Java code uses Customer objects, you should probably have methods that return Customer objects.

I'm no expert, but there's a lot of discretion involved. If you'd like to take a stab at designing it, and then post your idea here, I'm sure some members could offer some constructive criticism.

---

### Post by Some Penguin on 2012-12-16
Yup.  So if we had a basic data structure like

```

class Foo {
  private UUID id;
  private Blah someData;
  private Blah2 otherData...
 ...
}

```

there might be a client that has methods along the lines of  

```

void upsert(Collection<Foo> foos) throws IOException;
void removeById(Collection<UUID> ids) throws IOException;
void query(Query<Foo> fooQuery, Callback<Foo> callback) throws IOException, CallbackRefusedException;
int count(Query<Foo> fooQuery);

```

where the Query class basically encodes a collection of query properties such as predicate/value pairs, ordering, or limit (where properties are identified by e.g. bean property name, which may or may not be the same as a column name in the actual data store); and the Callback has a function which would be invoked on each matching result in a streaming fashion.  The Callback might accumulate values in a list, it might compute an aggregate, etc; the main caution is that careless use of callbacks which invoke additional queries produce JVM-side dependencies between calls in one or more storage layers that may produce undetectable deadlocks (because the dependency cycle is partly in the JVM, partly in the storage servers, rather than e.g. all visible to the same database server).

For things that have to be strictly in isolated transactions (e.g. find-and-modify sorts of operations) I'd normally make them their own dedicated methods rather than expose such things as raw locking predicates -- too easy for things to go wrong with multiple clients all attempting to manage locking.

What /wouldn't/ be in the API would be anything like a ResultSet or PreparedStatement, for instance.

---

### Post by slickymaster on 2012-12-17
> Usually I prefer to separate storage logic from application logic -- only the internals of the storage layer need to be aware of the exact data store and its uses. The storage API provides basic operations -- querying, insertions, updates, deletions -- without explicitly indicating how (e.g. it doesn't use any SQL-specific classes).

Some Penguin is absolutely correct.

There are advantages associated with storing queries on the server rather than on the client machine. It has to do with the network performance. Usually, users use the same queries over and over again. Frequently, different users are trying to access the same data. Instead of sending the same queries on the network repeatedly, it improves the network performance and executes queries faster if the queries are stored on the server where they are compiled and saved as stored procedures. The users can simply call the stored procedure with a simple command, like execute stored_procedure A, but the stored procedures should be made flexible so that different users are able to pass input information to the procedure in the form of arguments or parameters and get the desired output.

A stored procedure is built inside the database before you run your application. You access that stored procedure by name at runtime. In other words, a stored procedure is almost like a method you call in the database.

Stored procedures have the following advantages:
[LIST]
[*]Because the procedure is precompiled in the database for most database engines, it executes much faster than dynamic SQL. Even if your database does not compile the stored procedure before it runs, it will be precompiled for subsequent runs just like prepared statements.
[*]Syntax errors in the stored procedure can be caught at compile time rather than runtime.
[*]You only need to know the name of the procedure and its inputs and outputs. The way in which the procedure is implemented is totally irrelevant.
[/LIST]

---

### Post by kevinharper on 2012-12-17
Thank you Trent for the links. I need to take some time and re-read those. I also read about separation of concerns (a link off of one of the pages your posted).

Some Penguin & SlickyMaster. WHOA... :) Thank you, but whoa. I am wrestling with your suggestion. Here's what I understand:

If I have a LAMP server set up I can create a class on the server that holds the queries. From a client computer I would simply call a method on the queries class.

But I don't think that's what you mean.
SlickyMaster says, "Because the procedure is precompiled in the database for most database engines." What do you mean by precompiled IN the database?

Some Penguin says, "...and the Callback has a function which would be invoked on each matching result in a streaming fashion..." I have to not only create a method that executes a query but also program the control of matching queries with results?

I don't think I completely understood your guys' answers. I think I need some time to read and re-read them again.

---

### Post by trent.josephsen on 2012-12-17
I'll let slickymaster address your first question directly, but just mention that stored procedures are something I probably wouldn't worry too much about at this stage. They are an important topic, but they are server side. Since you're focusing on the application side, making stored procs for all the appropriate operations might be a bridge too far.

I had a long description of callbacks here but I don't think it was very clear or helpful. Maybe I'll leave that to someone with actual expertise...

---

### Post by kevinharper on 2012-12-18
So here's where I'm at...

I don't currently have a server to play with. At least not one which allows me to place server-side Java (servlets or whatever). The server is a GoDaddy web server that provides MySQL DBs for me to connect to remotely. I don't think I can do much more than that. At some point in the future, however, I would like to have my own server that I can play with. But I'm nowhere close to that yet.

Here's how I did SQL Queries:
DBQueries singleton class:
```
import java.sql.Connection;
import java.sql.ResultSet;
import java.sql.SQLException;
import java.sql.Statement;


public class DBQueries {
	//DB table definition constants
	...final/constant fields...
	
	private Connection con;
	private Statement stmt;
	private ResultSet rs;	
	private String query;
	
	//from users table
	private int    userID;
	private String userName;
	private String password;
	private String fullName;
	
	//from access_levels table
	private String accessLevel;
	
	//from trainings table
	private int    trainingID;
	private String trainingTitle;

	//from sections table
	private int    sectionID;
	private String sectionTitle;
	private String sectionContent;
	
	private static DBQueries instance = null;
	
	protected DBQueries(){
		//Prevent instantiation
	}
	
	public static DBQueries getInstance(){
		if(instance == null) {
	         instance = new DBQueries();
	    }
	    return instance;
	}
	
	public void setCon(Connection c){
		this.con = c;
	}
	
	...authUser()...
	
	/***
	 * getActiveSpecialists() gets a list of all active console users
	 *	MySQL Query:
	 *		retrieves the number of results and all users' full name.
	 * 
	 * Function returns an array with all users' full names.
	 **/
	public String[][] getActiveSpecialists(){
		String activeSpecialists[][] = null;
		
		int resultCount = 0;
		int numResultRows = 0;
		
		try {			
			this.query = "SELECT COUNT(*), " + USERS + ".id, full_name, access_level"
						+ " FROM " + USERS
							+ ", " + JOIN_USERS_ACCESS_LEVELS
							+ ", " + ACCESS_LEVELS
					 + " WHERE " + USERS + ".active=1"
					 	+ " AND " + USERS + ".id=" + JOIN_USERS_ACCESS_LEVELS + ".user_id"
					 	+ " AND " + ACCESS_LEVELS +".id=" + JOIN_USERS_ACCESS_LEVELS + ".access_level_id"
					 	+ " AND " + ACCESS_LEVELS +".access_level=\"specialist\""
					 + " ORDER BY full_name DESC";
			
			this.stmt = con.createStatement();
			this.rs = stmt.executeQuery(query);
			while(rs.next()){
				resultCount = rs.getInt(1);
				numResultRows = resultCount;
			}
//Keep for debug purposes			
//			System.out.println("number of rows returned: " + numResultRows);
			
			activeSpecialists = new String[numResultRows][2];
			
			this.query = "SELECT " + USERS + ".id, full_name"
					+ " FROM " + USERS
						+ ", " + JOIN_USERS_ACCESS_LEVELS
						+ ", " + ACCESS_LEVELS
				 + " WHERE " + USERS + ".active=1"
				 	+ " AND " + USERS + ".id=" + JOIN_USERS_ACCESS_LEVELS + ".user_id"
				 	+ " AND " + ACCESS_LEVELS +".id=" + JOIN_USERS_ACCESS_LEVELS + ".access_level_id"
				 	+ " AND " + ACCESS_LEVELS +".access_level=\"specialist\""
				 + " ORDER BY full_name ASC";
			
			this.stmt = con.createStatement();
			this.rs = stmt.executeQuery(query);
			
			int row = 0;
			while(rs.next()){
				activeSpecialists[row][0] = rs.getString("id");
				activeSpecialists[row][1] = rs.getString("full_name");

//Keep for debug purposes				
//				System.out.println("DBQueries.getActiveSpecialists() :: Row: " + row);
//				System.out.println("DBQueries.getActiveSpecialists() :: activeSpecialists[row][0]: " + activeSpecialists[row][0]);
//				System.out.println("DBQueries.getActiveSpecialists() :: activeSpecialists[row][1]: " + activeSpecialists[row][1]);
				row++;
			}
		}
		catch (SQLException e) {
			// TODO Auto-generated catch block
			e.printStackTrace();
		}
		
		return activeSpecialists;
	}
	
	...addNewUser()...
	
	...disableSpecialist()...
	
	...getActiveTrainingTitles()...
	
	...getActiveSectionTitles()...
	
	...getSectionContent()...
}
```
I know it should not have been a singleton class. It should have been a public class with static methods (a db query utility class).

Here is a class that calls the query class:
```
...imports...


public class LayoutManageUsers extends JPanel{
	String[][] activeSpecialists = {};
	
	...private fields...
	
	public LayoutManageUsers(){
		activeSpecialists = DBQueries.getInstance().getActiveSpecialists();
		
		...JPanel properties...
		
		//START: Dynamic list of active users
		this.setLayout(new BorderLayout());
		this.setPreferredSize(new Dimension(500, 500));
		this.setBackground(Color.WHITE);

		int evenOrOdd = 0;
		int userID;
		String userFullName;
		for(int row = 0; row < activeSpecialists.length; row++) {
			userID = Integer.parseInt(activeSpecialists[row][0]);
			userFullName = activeSpecialists[row][1];
			
			pnlActiveUser = new JPanel();
			pnlActiveUser.setLayout(new FlowLayout(FlowLayout.CENTER,0,0));
			pnlActiveUser.setPreferredSize(new Dimension(400, 37));
			
			//user full name layout
			pnlFullName = new JPanel();
			pnlFullName.setLayout(new FlowLayout(FlowLayout.LEFT,0,5));
			pnlFullName.setPreferredSize(new Dimension(190, 25));
			
			JLabel lblActiveUser = new JLabel();
			lblActiveUser.setText(userFullName);
			
			pnlFullName.add(lblActiveUser);
			
			//handle user button layout
			pnlHandleUser = new JPanel();
			pnlHandleUser.setLayout(new FlowLayout(FlowLayout.RIGHT,10,5));
			pnlHandleUser.setPreferredSize(new Dimension(190, 35));
			
			btnDisableUser = new MyDisableButton(userID);
			btnDisableUser.setText("Disable");
			
			pnlHandleUser.add(btnDisableUser);
			
			//alternate row border
			if(evenOrOdd%2 != 0)
				setBackground("WHITE");
			evenOrOdd++;
			
			pnlActiveUser.add(pnlFullName);
			pnlActiveUser.add(pnlHandleUser);
			
			pnlDContainer.add(pnlActiveUser);
        }
		// END: Dynamic list of active users
		
		this.add(pnlTitle, BorderLayout.NORTH);
		this.add(pnlDContainer, BorderLayout.CENTER);
		
		...Admin Panel if user is admin...
	}
	
	/***
	 * addUser() adds a new user when "Add User" button is clicked.
	 * Function verifies that no field was left blank.
	 **/
	private class addUser implements ActionListener{
		private boolean isFullNameValid = true;
		private boolean isUserNameValid = true;
		private boolean isPasswordValid = true;
		
		String fullName;
		String userName;
		String password; 
		
		@Override
		public void actionPerformed(ActionEvent ae){
			isFullNameValid = chkFullName();
			isUserNameValid = chkUserName();
			isPasswordValid = chkPassword();
			
			//display red backgrounds where errors found, return (exit)
			if(isFullNameValid == false || isUserNameValid==false || isPasswordValid == false){
				bgError(isFullNameValid, isUserNameValid, isPasswordValid);
				return;
			}
			
			fullName = txtNewUserFullName.getText().trim();
			userName = txtNewUserName.getText().trim();
			password = txtNewUserPassword.getText().trim();
			
			DBQueries.getInstance().addNewSpecialist(fullName, userName, password);
		}
	}
	
	/***
	 * chkFullName() checks input from txtNewUserFullName.
	 * It returns true if input is valid and false if invalid is detected.
	 **/
	private boolean chkFullName(){
		boolean isValid = true;
		
		if(txtNewUserFullName.getText().trim().equals(""))
			isValid = false;
			
		return isValid;
	}
	
	/***
	 * chkUserName() checks input from txtNewUserName.
	 * It returns true if input is valid and false if invalid is detected.
	 **/
	private boolean chkUserName(){
		boolean isValid = true;
		
		if(txtNewUserName.getText().trim().equals(""))
			isValid = false;
			
		return isValid;
	}
	
	/***
	 * chkPassword() checks input from txtNewUserPassword.
	 * It returns true if input is valid and false if invalid is detected.
	 **/
	private boolean chkPassword(){
		boolean isValid = true;
		
		if(txtNewUserPassword.getText().trim().equals(""))
			isValid = false;
			
		return isValid;
	}
	
	/***
	 * bgError() changes the background color of all text fields previously
	 * 	found to contain invalid data.
	 * @param validFullNameValid, validUserNameValid, validPasswordValid
	 **/
	private void bgError(boolean validFullNameValid, boolean validUserNameValid, boolean validPasswordValid){
		if(validFullNameValid == false){
			txtNewUserFullName.setBackground(Color.RED);
		}
		
		if(validUserNameValid == false){
			txtNewUserName.setBackground(Color.RED);
		}
		
		if(validPasswordValid == false){
			txtNewUserPassword.setBackground(Color.RED);
		}
	}
	
	/***
	 * setBackground() alternates background color or "rows" that display active users'
	 * 	names. It sets all panels' backgrounds to GRAY or WHITE.
	 */
	private void setBackground(String color){
		if(color.trim().equals("WHITE")){
			pnlActiveUser.setBackground(Color.WHITE);
			pnlFullName.setBackground(Color.WHITE);
			pnlHandleUser.setBackground(Color.WHITE);
		}
	}	
}
```

The "...whatever..." takes place of a whole block of code that does what the caption says.

---

### Post by slickymaster on 2012-12-18
> **kevinharper said:**
> SlickyMaster says, "Because the procedure is precompiled in the database for most database engines." What do you mean by precompiled IN the database?

Each SQL statement you send to the database needs to be parsed by the database engine before it can actually be executed. When the database parses a SQL statement, it reads the SQL to determine
what you want the database to do, and then it formulates a plan for carrying out your instructions. This processing is called building a query plan.
Each SQL statement you sent to the database required the database to treat the statement as a brand-new query and thus build a new query plan for it. If you are executing statements over and over
again that have the same query plan, you are wasting processing power.

Because stored procedure statements are stored directly in the database, built inside the database before you run your application, they may remove all or part of the compilation overhead that is typically required in situations where software applications send inline (dynamic) SQL queries to a database, thus executing much faster than dynamic SQL, which needs to be re-interpreted each time it is issued. Even if your database does not compile the procedure before it runs, it will be precompiled for subsequent runs.

---

### Post by kevinharper on 2012-12-18
@slickymaster,
NICE! Just went into my DB and created a test procedure.

Guess it's time to dive into [http://docs.oracle.com/javase/tutorial/jdbc/basics/storedprocedures.html](http://docs.oracle.com/javase/tutorial/jdbc/basics/storedprocedures.html)

Better yet, I think I should take some time to go through the whole JDBC tutorial.

@All,
So... here's what how I have to approach this:
1) My GUI classes interact with my logic classes that, in turn, interact w/ the database.
2) The logic classes manipulate data before forwarding to either the DB, or the GUI class that executed a query.

I'm sure a lot of this will be covered in the tutorial. Time to start reading.

---

### Post by trent.josephsen on 2012-12-18
I'll throw a few critiques your way.

For starters, you're right that it probably shouldn't be a singleton class, but I wouldn't make it a utility class either. Just leave it as a normal class. There's nothing preventing you from using two databases at once, using two separate instances of your class (which I'll call UserDAO to reflect its new purpose).

Your class has a bunch of fields that could be made local variables instead. There's no reason for the table data to persist between calls to different methods; if it's important, you should pass it as the return value of a function and let the client code keep track of it. Since you'll be creating a new statement, query and resultset for each new method call, the only field you really need is the Connection, which needs to persist for as long as the data access object lives. Speaking of which, you can pass the Connection in to the constructor or (if UserDAO is the only class that needs to access the database) create it inside the constructor.

I'm not going to talk about how you should rewrite getActiveSpecialists() because I guess you know it's horrendously inefficient. What I am going to complain about is that you're returning an array of String[]s when what you probably should be returning is a Collection of Users. getActiveSpecialists() should parse each row and spit it out in a form that the rest of your application can use directly. Maybe the rest of your application doesn't have a User class, in which case you should maybe redesign the whole thing. (Actually, maybe you should do that anyway. Design takes practice.)

There's a lot of discretion, too, in knowing when to parameterize and indirect and abstract and encapsulate and all that. For instance, you've made the name of your users table a... well, not quite a "parameter" since you have to edit the code to change it, but you've gone out of your way to make it easy to change. In my experience table names are not things that get changed often, so I'd favor readability in that case and make your entire SQL statement a literal string. On the other hand, you haven't parameterized the access level you select on, so you'd have to write an entirely new SELECT statement if you wanted to run the same code again but with access_level='guru'. With Perl's DBI, you could write something like this ($dbh is a database handle, which is basically the equivalent of a Connection)
```
# create a statement handle with a parameter
$sth = $dbh->prepare("SELECT
    users.id,
    users.fullname
FROM users JOIN acclevels ON
    users.id = acclevels.user_id
WHERE acclevels.access_level = ?");

# get users with the "specialist" access level
$sth->execute('specialist');
# get users with the "guru" access level
$sth->execute('guru');
```
In Java it's the same general idea but I think you have to use PreparedStatement. (I haven't actually done this in Java; can you tell?)

Don't get discouraged. This kind of thing is IMO a lot harder in Java than it really needs to be. If you know some Python or Perl you might consider making a quick prototype in one of those languages to see how different kinds of designs translate to different amounts of work. I wish I could show you some of the code I've worked on; it might help.

(Actually, a lot of my code uses DBIx::Class, which is a whole can of worms, but I still recommend it if you're doing significant amounts of database access in Perl. It's a lot cleaner than embedding SQL into Perl directly.)

PS since I didn't see your last post: I have heard the JDBC tutorial is good.

---

### Post by kevinharper on 2012-12-18
> I'll throw a few critiques your way.
Please don't ever hold back.

> I wouldn't make it a utility class either. Just leave it as a normal class
This is actually what I meant... I guess I'm unclear as to how to create a utility class. Basically a utility class has public static methods and cannot be instantiated, where the other (regular) class can... right?

> There's no reason for the table data to persist between calls to different methods; if it's important, you should pass it as the return value of a function and let the client code keep track of it
Agreed.

> you can pass the Connection in to the constructor or (if UserDAO is the only class that needs to access the database) create it inside the constructor.
So you're suggesting a the following class?:
```
...whatever imports are needed...

public class UserDAO{
    private Connection con;
    
    public UserDAO(Connection c){
        this.con = c
    }
    
    public List<Users> getActiveSpecialists(){
        ...Code for executing stored db procedures...
        ...Code for parsing through results...
        ...Code to return collection of users...
    }    
}
```
Then I would have the actual MySQL queries stored on the db, as slickymaster suggested.

> ...you should maybe redesign the whole thing. (Actually, maybe you should do that anyway. Design takes practice.)
Yeah... I agree, which is why I'm asking questions right now BEFORE I even start coding a redo of the project. I want to set it up correctly so I can just start coding away when the design is ready.

> For instance, you've made the name of your users table a... well, not quite a "parameter" since you have to edit the code to change it, but you've gone out of your way to make it easy to change
Not quite. I defined these as final/constants because the db requires me to user a db_name.tb_name everywhere I want to make reference to a table or column. So I really have to do db_name.tb_name.column_name. To lower my required typing, I created constants with the table names. So USERS is really cis279JAVA.users.

> With Perl's DBI...
I have actually done a little bit of perl and a little more PHP. It's been ages, but I do remember doing precisely what you did in your example.

And yes... The SQL cannot (and should not) be salvaged. I am very aware of that. Which is why I decided to ask questions about this topic (directly related to what I had already done).

> Don't get discouraged...
Not at all. I am barely getting started. First real programming I've done in almost 10 yrs. It'll come back. Rusty, just need practice. Not afraid to put in the time and effort required. And honestly, I would like to offer you the same piece of advice, :P. Don't get discouraged if I keep coming with more and more questions.

---

### Post by trent.josephsen on 2012-12-18
> **kevinharper said:**
> This is actually what I meant... I guess I'm unclear as to how to create a utility class. Basically a utility class has public static methods and cannot be instantiated, where the other (regular) class can... right?
Yep, pretty much.


> So you're suggesting a the following class?:

Pretty much exactly that, yes.


> Yeah... I agree, which is why I'm asking questions right now BEFORE I even start coding a redo of the project. I want to set it up correctly so I can just start coding away when the design is ready.
Smart.

> I defined these as final/constants because the db requires me to user a db_name.tb_name everywhere I want to make reference to a table or column. So I really have to do db_name.tb_name.column_name. To lower my required typing, I created constants with the table names. So USERS is really cis279JAVA.users.

Ah, I see... you may be able to omit that bit with the SQL USE statement, or by specifying it somehow when you connect. It may also depend on the DBMS you use. I didn't have to do that with my last SQL but I'm also a little rusty. That was also a rather different situation.

As for your SQL, it's a bit of a mess, but I've seen (and written) worse. I was more concerned with the design of the rest of your program. 

> I am barely getting started. First real programming I've done in almost 10 yrs. It'll come back. Rusty, just need practice. Not afraid to put in the time and effort required. And honestly, I would like to offer you the same piece of advice, :P. Don't get discouraged if I keep coming with more and more questions.
Not at all! Happy to help when I can. But don't necessarily take my word for things. Like I said in [another recent thread](http://ubuntuforums.org/showpost.php?p=12406175&postcount=2), I'm not a professional programmer, and this is the kind of thread where I have to speak very carefully because I don't want to give drive-by bad advice.

Best of luck.

---

### Post by kevinharper on 2012-12-18
> you may be able to omit that bit with the SQL USE statement, or by specifying it somehow when you connect. It may also depend on the DBMS you use. I didn't have to do that with my last SQL but I'm also a little rusty. That was also a rather different situation.
This really won't matter b/c I'll be setting up the queries as procedures directly on the DB.

And yes... the queries are fugly. When I created my first one I was very excited to get a result and be able to print it out. I texted it to my friend (a programmer by trait) and he said, "Wow. Looks like you wrote a novel to get a single row".

It's okay though. My code redo's are usually much, MUCH better than the previous version. All of you guys are awesome, btw. Thanks for the help.

---

### Post by Some Penguin on 2012-12-19
As long as you're willing to look around and redesign, you might want to have a look at [JDBI]("http://www.jdbi.org/"), which provides a more generally convenient and sane layer than raw JDBC access.

JDBC works, but it has a lot of warts... :/

One other note:  if your code explicitly throws around JDBC objects like Connections, Statements and ResultSets, be very very careful to use try/catch/finally blocks to ensure that they are eventually closed.  JDBC driver implementations tend *not* to use finalizers to automatically close such resources, and even if they did, finalizers are not guaranteed to run remotely promptly.  Also, while technically you should be allowed to assume that closing a Statement closes the associated ResultSet, and closing a Connection closes handles to any Statements (per the JDBC specifications)... I've run into at least one connection pool which for quite some time blatantly violated this in the name of performance, namely BoneCP.  Connection leaks aren't any fun to track down.

---

### Post by slickymaster on 2012-12-19
Following the previous posts, just wanted to say that one must always keep in mind the MVC (Model-View-Control) paradigm, especially when working with databases.

In this particular situation, my approach to what you are trying to accomplish would be to create three public interfaces:
**_UserWriter_**, that would contain three abstract methods addUser, updateUser and deleteUser. All three methods accept a User object as argument and return a boolean value that indicates whether any operation on the database was successful:
```
public interface UserWriter 
{
    boolean addUser (User user);
    boolean deleteUser (User user);
    boolean updateUser (User user);
} 
```
**_UserReader_** that would return an ArrayList of User objects or a single User object:
```
public interface UserReader 
{
    User getUser(int user_id);
    ArrayList<User> getUsers();
}
```
**_UserDAO_** that would extend UserWriter and UserReader interfaces thus providing indirectly the data access functions for the application:
```
public interface UserDAO extends UserReader, UserWriter
{    
}
```
Then I would create a class with a single method to return an object that implements the UserDAO interface so when the application calls this method it uses all the methods of this object to handle the data access for the application. This class is the linkage between the database and the rest of the application.:
```
public class DAOFactory 
{
    public static UserDAO getUserDAO()
    {
        UserDAO userDAO = new SQL_Slave();        
        return userDAO;
    }
}
```
Finally you would need a class that would communicate with the database on the server:
```
public class SQL_Slave implements UserDAO
{
    private DBslave slave = null;
    private ResultSet rSET = null;
    private CallableStatement cstmt = null;
    
    public SQL_Slave()
    {
        slave = new DBslave();
    }

    @Override
    public User getUser(int user_Id)
    {
        try 
        {
            User user = null;
            
            cstmt = slave.connect().prepareCall("{call dbo.GetUser(?)}");
            cstmt.setInt(1, user_Id);
            cstmt.execute();
            rSET = cstmt.getResultSet();
            while (rSET.next())
            {                
                int user_id = rSET.getInt(1);
                String user = rSET.getString(2);
                
                user = new User(user_id, user);
            }
            rSET.close();
            shutDownSlave(cstmt, slave);
            return user;            
        }
        catch (SQLException ex) 
        {
            return null;
        }
    }

    @Override
    public ArrayList<User> getUsers() 
    {
        try 
        {            
            ArrayList<User> users = new ArrayList<>();
            
            cstmt = slave.connect().prepareCall("{call dbo.GetUsers}");
            cstmt.execute();
            rSET = cstmt.getResultSet();
            while (rSET.next())
            {                
                int user_id = rSET.getInt(1);
                String user = rSET.getString(2);
                
                User user = new User(user_id, user);
                users.add(user);
            } 
            rSET.close();
            shutDownSlave(cstmt, slave);
            return entidades;
        } 
        catch (SQLException ex) 
        {
            return null;
        }
    }
    
    @Override
    public boolean addUser(User user)
    {
        try 
        {
            cstmt = slave.connect().prepareCall("{call dbo.AddUser(?)}");
            cstmt.setString(1, user.getUser());
            int success = cstmt.executeUpdate();
            switch(success)
            {
                case 1:
                    shutDownSlave(cstmt, slave);
                    return true;
                default:
                    return false;
            }
        } 
        catch (SQLException ex)
        {
            return false;
        }
    }
    
    @Override
    public boolean deleteUser(User user)
    {
       basically the same as addUser;
    }
    
    @Override
    public boolean updateUser(User user)
    {
        try 
        {
           cstmt = slave.connect().prepareCall("{call dbo.UpdateUser(?,?)}");
           cstmt.setInt(1, ent.getUser_Id());
           cstmt.setString(2, ent.getUser());
           int success = cstmt.executeUpdate();
           switch(success)
           {
               case 1:
                   shutDownSlave(cstmt, slave);
                   return true;
               default:
                   return false;
           }
        } 
        catch (SQLException ex)
        {
            return false;
        }
    }

    private void shutDownSlave(CallableStatement cSTMT, DBslave cONN)
    {
        try 
        {
            cSTMT.close();
            cONN.disconnect();
        } 
        catch (SQLException ex)
        {
            Logger.getLogger(SQL_Slave.class.getName()).log(Level.SEVERE, null, ex);
        }
    }
}
```
An of course a class to deal with the connection to database:
```
public final class DBslave
{
    private Connection conn = null;
    private static String connectionURL = "your connection string";
        
    public DBslave()
    {
        this.conn = connect();
    }

    public Connection connect()
    {
        try 
        {
            Class.forName("your driver");
            conn = DriverManager.getConnection(connectionURL);
        }
        catch (SQLException | ClassNotFoundException sqlEx) 
        {
            showMessage(sqlEx.getMessage());
        }
        return conn;
    }
    
    public boolean disconnect()
    {
        try 
        {
            if(conn != null) {
                conn.close();
            }
            conn = null;
        } 
        catch (Exception e) 
        {
            return false;
        }
        return true;
    }
    
    private static void showMessage(String msg) 
    {
        JOptionPane.showMessageDialog(null, msg);
        System.exit(0);
    }
}
```

---

### Post by trent.josephsen on 2012-12-19
I realize we're dealing with Java where overblown inheritance trees are the canonical way of doing absurdly simple things, but I still think three interfaces is a little bit unneccessary.

---

### Post by kevinharper on 2012-12-19
Read. Glad you interfaces. Will reply again after work.

---

### Post by slickymaster on 2012-12-19
> **trent.josephsen said:**
> I realize we're dealing with Java where overblown inheritance trees are the canonical way of doing absurdly simple things, but I still think three interfaces is a little bit unneccessary.

The reason for the three interfaces was just to make more clear the illustration of how works what was intended.
One thing has to be kept in mind though, there is the need for at least two interfaces. 

Since UserDAO is an interface, it can't directly provide the data access functions for the application. That's why the need for the SQL_Slave class. It implements the UserDAO interface by retrieving and saving the user data from the database.

What I regard as important in my example is the fact that the view layer of the application itself isn't aware of the specific class that provides the data access, it only knows the class it uses for data access implements the UserDAO interface.
But for me, the key is the DAOFactory class which returns an object that implements the interface discussed above, and uses the methods of that object to handle the data access for the application.
In short, this class (DAOFactory) insulates the view layer from the database layer of the application.

Keep in mind that I started my previous post referring to the importance of MVC (Model-View-Control) paradigm, especially when working with databases.

---

### Post by trent.josephsen on 2012-12-19
Conceded.

---

### Post by slickymaster on 2012-12-19
> **trent.josephsen said:**
> Conceded.

Do not misunderstand me, please. I was just trying to explain why I have designed the code that way and not trying to be stubborn or confrontational. If that was the image that transpired I apologize, it was not my intention.

---

### Post by trent.josephsen on 2012-12-19
Not at all. I agree there are good reasons for doing it the way you suggested. In this particular case I'd probably write UserDAO as a class, for the purpose of learning how DAOs work, and go back and change it to an interface (and perhaps add the factory) later if I found the need to do so. OP doesn't currently need to code to a particular API or be concerned about backwards compatibility. You can still keep M-V-C separated as long as your client code doesn't concern itself with how UserDAO works internally.

But you're right -- it's possible to design for flexibility from the start, and as long as OP isn't getting swamped in too much new information to make sense of it all, that's the smarter approach.

---

### Post by kevinharper on 2012-12-19
> ...and as long as OP isn't getting swamped in too much new information to make sense of it all, that's the smarter approach.
LOL. I read, and re-read most of your guys' posts. And then I read them 3 more times.

It is a lot of information but it is worth it.

I think this thread has evolved way beyond my initial post. And that is good. I really have found it educational. I'm starting to get stuck trying to fit this into the larger scheme, though.

Thanks to your responses, I have a very good idea of how to interact with the DB. Save procedures on the DB, call those procedures from DOA_slave classes that implements a DOA interface. And another class to handle the connect/disconnect to/from DB.

Very clean, very well explained, I like it.

I need a list of active specialists which, as you guys have suggested, should be a collection of objects. Why? Because I can manipulate it into whatever I need to anyways? Meaning that I should return an arraylist and have the calling class deal with it? Have that other class (the one receiving the arraylist) extract the information it needs?

I hope that question made sense.

I need to access the DB to log on. I need it to display a list of active users and give the admin a way to deactivate or edit current users, and add new users.

A successful login does create a singleton class. I need to set the login credentials once and have them available from EVERYWHERE (username, real name, & access level). This is one of few things that I do not plan on changing.

Here's what I will do. I'll get the users queries that we have been talking about here to work. I'll make this part functional and then post it so you can critique real work and we all have a base from which to launch/continue.

---

### Post by trent.josephsen on 2012-12-20
> **kevinharper said:**
> I need a list of active specialists which, as you guys have suggested, should be a collection of objects. Why? Because I can manipulate it into whatever I need to anyways?

Because a "user" is a **central idea** to the operation of your program (as I understand it) that is **not easily expressed either as a function or a single piece of data**. Those criteria are a strong hint that User should be a unique class. The OO paradigm is, loosely speaking, to *define the data types you will be using and operations associated with those types*. "User" sounds to me like a type you would want to have.

> A successful login does create a singleton class. I need to set the login credentials once and have them available from EVERYWHERE (username, real name, & access level). This is one of few things that I do not plan on changing.

If you really do need access to the database from *everywhere* in your program, that may itself be symptomatic of a design error. Keep MVC in mind -- the user interface code should be essentially ignorant of the database.

> Here's what I will do. I'll get the users queries that we have been talking about here to work. I'll make this part functional and then post it so you can critique real work and we all have a base from which to launch/continue.

Sounds like a plan. :)

---

### Post by slickymaster on 2012-12-20
> **kevinharper said:**
> I need a list of active specialists which, as you guys have suggested, should be a collection of objects. Why? Because I can manipulate it into whatever I need to anyways? Meaning that I should return an arraylist and have the calling class deal with it? Have that other class (the one receiving the arraylist) extract the information it needs?

trent.josephsen is right. In fact the concept of a User class to be instantiated as needed, is behind all the code I've posted.

> **kevinharper said:**
> ...display a list of active users and give the admin a way to deactivate or edit current users, and add new users.

I know that what is intended is an academic work, but this situation is a bit ungrateful because in a real context this particular job is always done by a database administrator on the server side.

---

### Post by kevinharper on 2012-12-20
It was indeed my final project for the Java class I took this semester (ended 1 wk ago).

But it was made with the intention of being able to use it at work. I asked a couple of people if they could think of an application that would make their job easier. The new-hire trainer said asked if I could make something to help him direct his trainings.

What I currently have works. But I want to eventually add more functionality to it. My original question on this thread was so that I could get an understanding about how to approach DBs from Java programs. Thanks to your awesome posts I think I have a very good understanding of how to go about it.

I think we started to focus on users a little prematurely. The class I put up where I show my queries was an example of what I did for the class. Again, I will admit, it is beyond fugly and I want to redo it before handing it to my coworker.

> I know that what is intended is an academic work, but this situation is a bit ungrateful because in a real context this particular job is always done by a database administrator on the server side.
I know that there are a lot of things going on here. Your guys' input has been more than plentiful. I will take a second look at my current DB tables and set up the procedures.

When I do, I'll post the table names, their columns, and the DB procedures. Hopefully I can also get the Java classes done. If so, I will post those as well. :) Then I can move on to something else.

PS: To answer the whole user/object questions. The person using the software is the User. He/She logs in. If successful, information gets sent to User. If this user's permission level is trainer or admin, he/she can disable and edit current users. He/She can also create new users. I understand THE USER needs his/her own class, but my previous question was about whether each result row really needed to be an object.

You guys are the best. I've learned a whole lot on this thread. Thank you.

---

### Post by slickymaster on 2012-12-21
I am glad I could have helped somehow.

> **kevinharper said:**
> Again, I will admit, it is beyond fugly and I want to redo it before handing it to my coworker.

Learning a new programming language is like everything in life, trial and error.
One of the things I find extremely rewarding is to read code applications written &#8203;&#8203;by good programmers and essentially to write, and write, our own code. Time and experience are the best teachers, especially in a language like java and particularly in the java integration with databases.

---

### Post by slickymaster on 2012-12-21
Ups... forgot one thing. Maybe now you could mark this thread as SOLVED.

---

### Post by trent.josephsen on 2012-12-21
> **kevinharper said:**
> PS: To answer the whole user/object questions. The person using the software is the User. He/She logs in. If successful, information gets sent to User. If this user's permission level is trainer or admin, he/she can disable and edit current users. He/She can also create new users. I understand THE USER needs his/her own class, but my previous question was about whether each result row really needed to be an object.

Yep, that's the question I answered. "The user" as in the person interacting with your UI doesn't need to be a class; that user does not represent data in your program.

But go ahead and work out a design and we can continue this conversation with a basis for improvement. :)

---

### Post by 1clue on 2012-12-21
If you're talking about making this into a production-ready application, why not use ibatis or hibernate?  Either of these approaches is common.  We use both depending on the circumstances.  I use groovy/grails instead of Java for this because it's much easier, but both these technologies are available in Java.

Ibatis lets you externalize your SQL into an XML-style object.  Then it populates a list of some class (could be a hashmap or a pojo specifically set up as a domain class).

hibernate lets you use a domain class which is basically a POJO.  You do something like:

Customer customer = Customer.get(123)
customer.address1 = '1234 some street'
customer.address2 = 'suite 110'
...
customer.persist(flush:true)

and all the sql is handled for you, automatically, and you need not code around specific database or dialect.  The hibernate data source is set up at the beginning of the application run (again in a separate config file) and everything in the app uses it.

---

### Post by kevinharper on 2012-12-22
@1Clue:
Someone else had suggested something similar to me previously (another thread). Their suggestion was JPA2. Worked very similar to your example.

This is definitely something I will consider for a future 'version'. There is always something that can be improved. It's time for me to stop looking for improvements and start coding.

@Slickymaster, I hadn't set this as solved because I wanted to continue adding to it when I complete my DB stuff this weekend. But you're right. I'll set it to solved and just create a "Code Audit" thread when it's ready.

@Trent
> that user does not represent data in your program.
True. But the program needs to know the user's real name and access level to determine what GUI components to display. But that's beyond the scope of this thread. :) I'll ask when the time comes, I'm sure of it.

PS: I ended up w/ an A in the class.

---

### Post by 1clue on 2012-12-22
Kevin,

Congratulations on the A.

Real-world programming, you never have a finished project.

We have a few very large applications.  We separate our ibatis queries into files based either on the service they're used by, or by some other concept which makes sense.  You can't expect to have a one-size-fits-all approach, each situation needs a fresh look.

---

### Post by slickymaster on 2012-12-22
> **kevinharper said:**
> PS: I ended up w/ an A in the class.

Congratulations on your grade. I think it's trully deserved.

And when the time came, when you'll open that other thread, I'll be glad to help in anyway necessary.

---

### Post by kevinharper on 2012-12-22
> **1clue said:**
> Real-world programming, you never have a finished project.
I completely agree. But you can't update something until it has already been implemented. I will be looking into your suggestions. I'm hope to be able to rely on them when I want to make my next set of revisions.

Thanks everyone.

---

