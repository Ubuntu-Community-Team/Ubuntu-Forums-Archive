---
title: "[Beginner] Programming Challenge: 7"
date: 2008-10-07
forum: Programming Talk
---

### Post by LaRoza on 2008-10-07
This new challenge with be something useful. It will be dealing with databases. This means, you will have to learn a new API (don't worry, they are usually very simple) and possibly a bit of SQL, although you can get around that with various modules.

[size=+1]The Challenge[/size]
Write a program which takes two input fields, name and age. Name with be a string (assume that 64 characters is the limit, if you need a limit), age will be a positive integer. 

After checking if the data is valid, the program will put them in a database. 

The program will have to somehow also be able to retrieve the records and output them. I suggest a simple text interface:

```

Ask user if they want to input data or retrieve
                       |
                       |
_______________________|_______________________
|                                             |
|                                             |
Retrieve: Output all                        Input 
records neatly                                |
                                Get names ____|____ Exit on "exit"
                                and ages, 
                                validating 
                                as it goes


```


[size=+1]The Reasons[/size]
This challenge has aspects of the others. A new API, a new language (possibly, but SQL isn't hard at all), input, and it will benefit from structured programming.

Databases are extremely useful and knowing how to use them will help anyone.

[size=+1]Hints:[/size]
This challenge will be easiest with high level languages. I recommend sqlite, because it is small and very easy to use. See [http://laroza77.wikidot.com/sql](http://laroza77.wikidot.com/sql) on database engines/libraries and how to use SQL (see the individual modules for the language on the interfaces).

Some languages come with database capabilities. Java and Python are two that I know.

This database will be one table, one text field and one integer field.

[size=+1]How it will be graded[/size]
It won't be. You'll get feedback (hopefully) from those who can give it. You should focus on learning and trying to use new concepts.

---

### Post by OutOfReach on 2008-10-07
Mmm, databases. This is a good excuse for me to get familiar with them.

---

### Post by Sinkingships7 on 2008-10-07
WHOA! Now I'm excited!

I've never had the chance to practice with databases before, so this will be a first. I'm going to think about how I'm going to go about designing this while I sleep tonight, and get to work tomorrow.

Thanks again, LaRoza!

---

### Post by TreeFinger on 2008-10-07
I am pretty excited for this project. Hopefully this will motivate me to set up my box that is marked to be a web server / db server :)

---

### Post by ghostdog74 on 2008-10-08
A prehistoric and simple sequential database, dBase.
```

<?php
if( isset($_POST["submit"]) ){
    if ( (!empty($_POST['username']) && strlen($_POST['username']) <=64) &&
       ( !empty($_POST['age']) && $_POST['age']< 100 ) )        
    {    
        $dbfields = array(
            array("username","C",64),
            array("age","N",3,0)
        );
        define("USERDB", "/tmp/userdb.dbf");
        if( !file_exists(USERDB) ) {
            if ( !dbase_create(USERDB,$dbfields) ){                            
                echo '<p>Cannot create database</p><br/>';
                exit();
            }else{
                    //create dummy user at first time use,open db for r,w
                    $dbid = dbase_open(USERDB,2);
                    $dummy= array( "dummy",1.0);
                    dbase_add_record($dbid,$dummy);
                    dbase_close($dbid);            
            }
        }
        
        $username = trim($_POST['username']);
        $age = trim($_POST['age']);
        //found user flag.
        $found=0;

        //open database r,w and retrieve information from db
        if ( $dbid = dbase_open(USERDB,2) ){
            $recnum = dbase_numrecords($dbid); 
            for($i=1;$i<=$recnum;$i++){
                $row = dbase_get_record_with_names($dbid,$i);
                $rname = trim($row['username']);
                $rage= trim($row['age']);
                if  ( $rname == $username){
                    echo '<h1><p>Found userName: '.$rname.' , Age: '.$rage.'</p></h1><br/>';
                    $found=1;
                    break;
                }
            }
            if ( !$found ){
                echo '<h1><p>Created user: '.$username."Age: $age</p></h1><br/>";
                $record = array($username,$age);
                dbase_add_record($dbid,$record);               
                dbase_close($dbid);
            }
            
        }else{
            echo '<p>Error opening database</p>';
        }
        
    }else{
        echo '<p>Invalid input</p>';   
    }
        
    
}else{
?>
    <!-- show form -->
    <html><head>
            <title>Demo DBase (DBM style) database</title>
          </head>
    <body>
            <form action="<?php echo $_SERVER['PHP_SELF']?>" method="POST">
                <table align="left">
                <tr>
                    <td>Enter name:</td>
                    <td><input name="username" maxlength="64" size="64" type="text" />
                </tr>
                <tr>
                    <td>Age:</td>
                    <td><input name="age" size="3" maxlength="3" type="text" />
                </tr>                
                <tr>
                    <td colspan="2">
                        <input type="submit" name="submit">
                    </td>
                </tr>
                </table>

            </form>
    
    </body>
    </html>
    
<?php
}
?>

```

---

### Post by MacUntu on 2008-10-08
> **LaRoza said:**
> but SQL isn't hard at all
I'd be careful about saying that (unless you ment the syntax). ;)

---

### Post by LaRoza on 2008-10-08
> **MacUntu said:**
> I'd be careful about saying that (unless you ment the syntax). ;)

Well, the level of understanding needed for this challenge.

---

### Post by jimi_hendrix on 2008-10-08
do i have to use a database or can i create my own file extension file (.data) and parse it?

---

### Post by LaRoza on 2008-10-08
> **jimi_hendrix said:**
> do i have to use a database or can i create my own file extension file (.data) and parse it?

You don't have to do anything ;) The point of the exercise is using a database, not getting around using one though.

Although it isn't stated, an additional requirement was going to be to allow people to use the application to get the ages of people whose names are entered or to get all people of inputted ages.

---

### Post by jimi_hendrix on 2008-10-08
odd...i cant figure out how to install sqlite...none of the files i try will install it

---

### Post by LaRoza on 2008-10-08
> **jimi_hendrix said:**
> odd...i cant figure out how to install sqlite...none of the files i try will install it

Search in synaptic?

Also, Python comes with it.

---

### Post by jimi_hendrix on 2008-10-09
thank you...was not at a linux computer so no synaptic

---

### Post by OutOfReach on 2008-10-09
Anyone know of a good Python + Sqlite tutorial? :)

---

### Post by SteelDragon on 2008-10-09
> **OutOfReach said:**
> Anyone know of a good Python + Sqlite tutorial? :)

Here is the one I used:
[URL="http://www.devshed.com/c/a/Python/Using-SQLite-in-Python/"]
http://www.devshed.com/c/a/Python/Using-SQLite-in-Python/[/URL]

Also, here is my attempt at this challenge. I hope that I'll add the query support that LaRoza mentioned, but this is all I have time for now and I wanted to get the bulk of it up for feedback.

There must be a better way of handling the database connection than passing it all over the place the way I've been doing. Any ideas? I thought of creating a class with methods to insert and query from the database, but I'm not sure if that's the ideal way.

The program uses the database my.db, creating it if it doesn't exist.

As always, a big thank you to LaRoza and to anybody with feedback and advice.

[PHP]#!/usr/bin/python

import pysqlite2.dbapi2 as sqlite
import os

def connect_to_db(filename):
    if not os.path.exists(filename):
        create_db(filename)

    return sqlite.connect(filename)

def create_db(filename):
    if os.path.exists(filename):
        return False
    db = sqlite.connect(filename)
    db.execute("CREATE TABLE main ('name' NOT NULL, 'age' INTEGER NOT NULL)")

def insert_record(db, name, age):
    db.execute('INSERT INTO main VALUES (?, ?)', (name, age))
    db.commit()

def get_records(db):
    cursor = db.execute('SELECT * FROM main')
    return cursor.fetchall()

def iface_input(db):
    os.system("clear")
    people = []
    name = raw_input("Enter the first name. Type 'exit' to quit. > ")
    while name.lower().strip() != 'exit':
        verified = False
        while not verified:
            age = raw_input("Enter " + name + "'s age. > ")
            if age.strip().isdigit():
                people.append((name, age))
                verified = True
            else:
                print "Ages must be entered as positive integers. Please try again."
        name = raw_input("Enter the next name. Type 'exit' to quit. > ")

    for person in people:
        insert_record(db, *person)
    print "Names entered."
    iface_main(db)

def iface_retrieve(db):
    os.system("clear")
    records = get_records(db)
    nameLength = 0
    for record in records:
        if len(record[0]) > nameLength:
            nameLength = len(record[0])
    print "Name".ljust(nameLength), "Age".rjust(11)
    for record in records:
        print record[0].ljust(nameLength), '===>', str(record[1]).ljust(5)

    print '\n\n'
    raw_input("Press Enter to return to Main Menu.")
    iface_main(db)

def iface_main(db):
    os.system("clear")
    print "What would you like to do?"
    print "     1 Input data"
    print "     2 Retrieve data"
    print "     3 Quit\n\n"

    verified = False
    while not verified:
        option = raw_input("Enter the number of your choice. > ")
        option = option.strip().rstrip('.')
        if option == '1':
            verified = True
            iface_input(db)
        elif option == '2':
            verified = True
            iface_retrieve(db)
        elif option == '3':
            import sys
            sys.exit()
        else:
            print "Please choose a number from 1 to 3."

if __name__ == "__main__":
    db = connect_to_db("my.db")
    iface_main(db)[/PHP]

Edit: Added a commit() to the insert_record() function, so that data persists from session to session. Also fixed the output formatting to make it look better. Still not as good as OutOfReach's, but not too bad.

---

### Post by LaRoza on 2008-10-09
> **OutOfReach said:**
> Anyone know of a good Python + Sqlite tutorial? :)

My wiki? [http://laroza77.wikidot.com/sqlite](http://laroza77.wikidot.com/sqlite)

---

### Post by nvteighen on 2008-10-09
This may be an interesting job for the Query language described at [http://mitpress.mit.edu/sicp/full-text/book/book-Z-H-29.html#%_sec_4.4.1](http://mitpress.mit.edu/sicp/full-text/book/book-Z-H-29.html#%_sec_4.4.1)

---

### Post by SteelDragon on 2008-10-09
> **nvteighen said:**
> This may be an interesting job for the Query language described at [http://mitpress.mit.edu/sicp/full-text/book/book-Z-H-29.html#%_sec_4.4.1](http://mitpress.mit.edu/sicp/full-text/book/book-Z-H-29.html#%_sec_4.4.1)

That looks cool. I may just have to do this challenge again ;-).

On a related note, after the last programming challenge I started looking into Lisp and came across the book in your link, as well as [How to Design Programs]("http://www.htdp.org"), which appeared pretty similar to my eyes. Since I know nothing about Scheme and little about programming at all, I couldn't make an educated as to which to read first. For some reason which I can't remember, I opted for HTDP and am working through it now. Any opinions on which is better or what significant differences there are between the two? That query language example looked really cool and handy, and if I don't come across something that impressive in my book, I'll regret my choice :). I intend to stick it out and have bookmarked SICP for later, so I'd really like knowledgeable opinions on either of both sources.

Cheers.

---

### Post by OutOfReach on 2008-10-09
Here's mine after some hours of reading and practice:

[PHP]
import pysqlite2.dbapi2 as sqlite
import os


class Database(object):
    
        def __init__(self):
            self.setup()
            self.user_input()
        
        def setup(self):
            exists = None
            if not os.path.exists("Name_Age.db"): exists = False
            self.connection = sqlite.connect("Name_Age.db")
            self.cursor = self.connection.cursor()
            if exists == False: 
                self.cursor.execute('CREATE TABLE information (id INTEGER PRIMARY KEY, name VARCHAR(50), age VARCHAR(50))')
            del exists

        def writeToDatabase(self):
            try:
                name = str(raw_input("What is your name?: "))
                age = int(raw_input("Your age?: "))
            except Exception, e:
                print "Wrong Input"
            self.cursor.execute('INSERT INTO information VALUES (null, ?, ?)', (name, age))
            self.connection.commit()
        
        def read_database(self):
            self.cursor.execute("SELECT * FROM information")
            for x in self.cursor:
                print "-"*10
                print "Name: %s" % x[1]
                print "Age: %s" % int(x[2])
                print "-"*10

        def user_input(self):
            choice = raw_input("Would you like to read your database or write to it? [r|w]: ")
            if choice.lower() in ("r", "read", "1"):
                self.read_database()
            elif choice.lower() in ("w", "write", "2"):
                self.writeToDatabase()
        
if __name__ == "__main__":
    Database()[/PHP]


Learning SQLite was much easier than I thought it would've been. :S

---

### Post by ghostdog74 on 2008-10-10
> **OutOfReach said:**
> Here's mine after some hours of reading and practice:

why are you putting your database statements inside the class?

PHP alpha version
```

<?php
$db  = "names.db";
$tablename="names";
if ( $dbh = sqlite_open($db,0666,$sqliteerror) ){
    $result = sqlite_query($dbh,"SELECT name FROM sqlite_master WHERE type='table' AND name='$tablename'");
    if ( sqlite_num_rows($result) <= 0){
        $cmd = "create table names( name VARCHAR(30) NOT NULL, age INTEGER NOT NULL)";
        $q = sqlite_query($dbh,$cmd);      
    }
    
}
echo "Enter name: ";
$name = trim(fgets(STDIN));
echo "Age: ";
$age = trim(fgets(STDIN));
print "Your name is ".$name." and age is: ".$age."\n";
if ( (!is_numeric($age)) || $age>130 || strlen($name) > 64 ){
    echo "Invalid input.\n";
    exit();
}
$q = "select * from '$tablename' where name = '$name'";
$result = sqlite_query($dbh,$q);
if ( sqlite_num_rows($result) > 0){
    while ( $row = sqlite_fetch_array($result,SQLITE_ASSOC) )  {
        echo 'Name: ' . $row['name'] . ' Age: ' . $row['age']."\n";
    }
}else{
   
    $q = "insert into names values('$name',$age)";
    $result = sqlite_query($dbh,$q);
}
sqlite_close($dbh);
        
?>

```

---

### Post by nvteighen on 2008-10-10
> **SteelDragon said:**
> That looks cool. I may just have to do this challenge again ;-).

On a related note, after the last programming challenge I started looking into Lisp and came across the book in your link, as well as [How to Design Programs]("http://www.htdp.org"), which appeared pretty similar to my eyes. Since I know nothing about Scheme and little about programming at all, I couldn't make an educated as to which to read first. For some reason which I can't remember, I opted for HTDP and am working through it now. Any opinions on which is better or what significant differences there are between the two? That query language example looked really cool and handy, and if I don't come across something that impressive in my book, I'll regret my choice :). I intend to stick it out and have bookmarked SICP for later, so I'd really like knowledgeable opinions on either of both sources.

Cheers.
Take also a look at the SICP videos 8a and 8b at [http://groups.csail.mit.edu/mac/classes/6.001/abelson-sussman-lectures/](http://groups.csail.mit.edu/mac/classes/6.001/abelson-sussman-lectures/) (well, better take a look at all of them... they're great "programming in general" lectures and also great Scheme lectures).

---

### Post by nuclearj on 2008-10-11
Hi all, here is my entry, it is not complete.  I am going out tonight, working tomorrow, and going to the Eagles game on Sunday.  So I'll be a little busy.  Anyways, once I get back I'll add the error checking and the displaying of the data in a nice neat fashion.

Well for the database part I used buzhug.  I am very new to programming so don't bust...  Looks like my code is the simplest though...

You have to install buzhug for this to work, [http://buzhug.sourceforge.net/](http://buzhug.sourceforge.net/)

```

from buzhug import Base

db = Base('pyProgChal').create(('name',str),('age',int),mode='open')

def inputData():
	global db
	name = str(raw_input('Please enter name: '))
	age = int(raw_input('Please enter age: '))
	db.insert(name,age)
	menu()

def retrData():
	global db
	nameData = db.select(['name'])
	ageData = db.select(['age'])
	print nameData
	print ageData
	menu()

def menu():
	menu = """
	Please make a selection:
		1) Input Data
		2) Retreive Data

		0) Exit
	"""

	start = int(raw_input(menu))
	# try statement to capture incorrect entries

	if start == 1:
		inputData()
	elif start == 2:
		retrData()
	elif start == 0:
		import sys
		sys.exit
	else:
		print 'Please select 1, 2, or 3'
		

if __name__ == "__main__":
	menu()

```

---

### Post by OutOfReach on 2008-10-11
> **ghostdog74 said:**
> why are you putting your database statements inside the class?


For no reason at all really.

---

### Post by LaRoza on 2008-10-11
> **OutOfReach said:**
> For no reason at all really.

Shame on your for not having world class code in a beginner challenge!

Yes, SQLite is very easy and handy :-)

---

### Post by indecisive on 2008-11-10
I am trying to use SQLite in Perl and I am having trouble installing the necessary modules from CPAN.  Any help?

---

### Post by indecisive on 2008-11-11
Is there a new challenge or has everyone just become bored?  Anyway, here is my submission (run it from wherever; it will put the SQLite database in your home directory).

BE SURE TO INSTALL DBI AND DBD::SQLite VIA CPAN!

challenge.pl:

```
#!/usr/bin/perl

use diagnostics;

use DBI;

sub ask_command()
{
	print "(store/get/exit/new):\t";
	$response=<STDIN>;
	chomp($response);
	$response;
}

sub is_new()
{
	$dbh->do("CREATE TABLE people (name, age);");
}

sub store_entry()
{
	print "NAME:\t";
	chomp($name=<STDIN>);
	print "AGE:\t";
	chomp($age=<STDIN>);
	$dbh->do("INSERT INTO people VALUES ('$name',$age)");
}

sub get_entry()
{
	print "(name/age/all):\t";
	chomp ($name_age=<STDIN>);
	
	if ($name_age eq 'name')
	{
		print "NAME:\t";
		chomp($name=<STDIN>);
		my $all=$dbh->selectall_arrayref("SELECT age FROM people WHERE name = '$name'");
		foreach my $row (@$all)
		{
			($age)=@$row;
			print "AGE:\t$age\n";
		}
	}
	if ($name_age eq 'age')
	{
		print "AGE:\t";
		chomp($age=<STDIN>);
		my $all=$dbh->selectall_arrayref("SELECT name FROM people WHERE age = $age");
		foreach my $row (@$all)
		{
			($name)=@$row;
			print "NAME:\t$name\n";
		}
	}
	if ($name_age eq 'all')
	{
		my $all=$dbh->selectall_arrayref("SELECT name, age FROM people");
		foreach my $row (@$all)
		{
			($name,$age)=@$row;
			print "NAME:\t$name\nAGE:\t$age\n";
		}
	}
}

$dbh=DBI->connect("dbi:SQLite:dbname=/home/$ENV{LOGNAME}/names.sqlt","","", { RaiseError => 1, AutoCommit => 1});

print "\n\tWelcome to Challenge7!  If you have not yet created your names and ages table, enter 'new' in the following prompt to do so.  Otherwise, select 'store' to store rows, 'get' to retrieve all rows or filter by name or age, and 'exit' to leave this program.  Your empty database (without the necessary table) has already be created if it did not already exist in '/home/$ENV{LOGNAME}/names.sqlt' Enjoy, and please have the courtesy to file a bug report if you find a bug.\n\n";

$command=&ask_command;

while ($command ne 'exit')
{
	if ($command eq 'new')
	{
		is_new();
	} else
	{
	if ($command eq 'store')
	{
		store_entry();
	} else
	{
	if ($command eq 'get')
	{
		get_entry();
	}
	}
	}
	$command=&ask_command;
}
```

---

### Post by run1206 on 2008-11-11
yeah i was wondering if a new challenge would be given yet...

:?

---

### Post by indecisive on 2008-11-15
LaRoza was banned, that must be why.

---

### Post by nvteighen on 2008-11-15
> **indecisive said:**
> LaRoza was banned, that must be why.
?

Anyone is free to post a challenge... (I'd do, but have no idea on what :p)

---

### Post by jimi_hendrix on 2008-11-15
how bout something that isnt math related like most challanges are...i mean strictly math related (as in calculate...)

---

### Post by shinook on 2013-02-06
Here is my attempt for this Challenge, I'm using Python 3.2.

```

# Beginner programming challenge 7

from sqlite3 import dbapi2 as sqlite
import sys

connection = sqlite.connect("test.db")
cursor = connection.cursor()

print("Welcome. Type 'r' to print the database or 'w' if you want to add data.\nType 'q' to exit.\n")


def get_choice():
    global choice
    choice = input("Please type 'r','w', or 'q': ")
            
    if choice in ("r","w","q"):
        pass
    else:
        print("This is not a valid command.")
        get_choice()
    

def get_name():
    uinput = input("Please type a name: ")

    global name
    name = str(uinput)


def get_age():
    uinput = input("Please enter an age higher than 0 (100 max): ")

    try:
        global age
        age = int(uinput)
    except ValueError:
        print("You must type an integer!")
        get_age()
        
    if age < 1 or age > 100:
        print("This is not a valid age.")
        get_age()



try:
    cursor.execute("create table data(NAME,AGE)")
except: # if the table already exists
    pass

get_choice()


while choice == "w":
    get_name()
    get_age()
    cursor.execute("insert into data values(?,?)",(name,age))
    connection.commit()

    print("Type 'w' again to add more data, 'r' to print or 'q' to exit.")
    get_choice()


if choice == "r":
    cursor.execute("select * from data")
    for row in cursor:
        print ("-"*20,'\nName:', row[0],'\nAge:', row[1])
        print("-"*20)


cursor.close()
connection.close()

if choice == "q":
    sys.exit(0)

```

---

### Post by howefield on 2013-02-06
Old thread closed.

---

### Post by Elfy on 2013-02-06
Staying closed.

If people want to run the same thing and refer to this then do so.

---

