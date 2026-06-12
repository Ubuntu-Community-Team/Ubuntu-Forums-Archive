---
title: "Object oriented programming,"
date: 2007-11-20
forum: Programming Talk
---

### Post by Mr.popo on 2007-11-20
:( I find it hard O O P hard and dont really undertstand it. Please can someone explain to me O O P in the simplest way so i could undertsand it better. If there are any tutorials which OOP mainly please could link me thanks.
This is for python :)
thanks.

---

### Post by slavik on 2007-11-20
if you understand what a struct (in C is) then OOP is really easy.

OOP is really just syntactic sugar.

C sample OO (I am assuming malloc is successful for obvious reasons).
struct myclass *s = (struct myclass*)malloc(sizeof(struct myclass));
do_something(s);

C++ (Python is not far from this syntax I think) sample OO
s = new myclass();
s.do_something();

think of a C struct as a hash with key, value pairs.

basically, a class has some definition of what data it has and what functions (called methods in OO) apply to it ...

class blah {
  int ha;
  int no;
  void do_something { do something ...; }
};

I am sorry this is not a better explanation :(

---

### Post by geirha on 2007-11-20
This looks like a good starting place to grasp the concept: [http://en.wikiversity.org/wiki/Object_Oriented_Software_Design](http://en.wikiversity.org/wiki/Object_Oriented_Software_Design)

---

### Post by pmasiar on 2007-11-20
O'Reilly has many good books. "Head First" series is excellent, HF OOP is one of best intro to OOP I've seen. Sadly, it is for Java :-(

OOP for different languages has different "feel", ie in Python you can mix old-style procedural and OOP programming while in Java you cannot. What language do you use?

---

### Post by LaRoza on 2007-11-20
> **pmasiar said:**
> What language do you use?

Python (I already asked in another thread)

---

### Post by pmasiar on 2007-11-20
In Python, you can use existing OOP modules, but not create your own until you are comfortable with OOP and it makes sense. Until then, you can hold you 'object' data in dictionaries and pass them around. Don't force OOP on yourself, it is in fact mostly syntax sugar around dictionaries.

I just found: [OOP is Namespace Oriented Programming](http://www.artima.com/forums/flat.jsp?forum=270&thread=216587)

and comment #23: "Object-orientation provides method dispatch."

---

### Post by dwhitney67 on 2007-11-21
OOP = Object Oriented Programming
OOD = Object Oriented Design

The language one chooses is dependent upon the requirements of the project, the computing environment, etc.

For OOD/OOP, you need to think in layman's terms; in other words, in terms of "is a" and "has a".

Think of an abstract object, such as a Shape.  A Rectangle _is a_ Shape, as is a Square, and a Square is a Rectangle (with equal sides); however a Rectangle is _not_ a Square.  Other examples of "is a" relationships to Shapes are the Triangle, the Circle, and the Ellipse.  (Actually, an Ellipse is a type of Circle!)

These shapes may have attributes; for instance, height, width, radius, etc. (this varies with the type of object).  But one thing they could have in common is a Point (x and y coordinates).  The may also have a Color attribute.

These attributes may be simple data types (integer, float, etc) or they may be complex objects.  These represent the "has a" relationship.

If you can understand the concepts above, then you have a grasp of OOD concepts.  You can represent a design using UML (Unified Modeling Language) to make things clearer.

As for the time when OOP comes into play, if you have a solid design, the choice of an OO language should not matter.  The "is a" relationship is represented by inheritance.  So in C++, something like this would be appropriate for the design above:

```
class Shape
{
  public:
    // all shapes occupy a certain area; thus require them to implement
    // a method that provides this information.
    virtual double computeArea() = 0;

  protected:
    // this is protected (so that one cannot instantiate this object), however
    // this is overkill since the object would not be able to be instantiated
    // anyhow because it is an abstract class.
    Shape( int x = 0, int y = 0);

    int getXCoord() const;
    int getYCoord() const;

  private:
    int x;   // this demonstrates the "has a" relationship
    int y;   // as does this
};

class Rectangle : public Shape          // this demonstrates the "is a" relationship
{
  public:
    Rectangle( double length, double height );

    virtual double computeArea();

  private:
    double length;   // another example of the "has a" relationship
    double height;
};

class Square : public Rectangle      // an "is a" relationship
{
  public:
    Square( double lengthOfSide );
};
```

Anyhow, I hope this basic description helps.  Do not try to over-complicate OOD and OOP.  Knowing how to represent your OOD thoughts using UML is very helpful.  The next time you have a chance, examine your surroundings to conjure up other "is a" and "has a" relationships (e.g. a Car is a Vehicle; a Boat is a Vehicle; but a Car is not a Boat... well, sometimes it is!).

---

### Post by LaRoza on 2007-11-21
> **dwhitney67 said:**
> Other examples of "is a" relationships to Shapes are the Triangle, the Circle, and the Ellipse.  (Actually, an Ellipse is a type of Circle!)


Actually, they are both Conic Sections, along with a few others. An circle is more of an ellipse with the two foci in the same point, I would say a circle is a special type of ellipse.

---

### Post by dwhitney67 on 2007-11-21
I have no idea what this has to do with the original topic, but from Wikipedia:
[I]
If the two foci coincide, then the ellipse is a circle; in other words, a circle is a special case of an ellipse, one where the eccentricity is zero.[/I]

So I guess you are correct.

---

### Post by aquavitae on 2007-11-21
> **dwhitney67 said:**
> I have no idea what this has to do with the original topic, but from Wikipedia:
[I]
If the two foci coincide, then the ellipse is a circle; in other words, a circle is a special case of an ellipse, one where the eccentricity is zero.[/I]

So I guess you are correct.Yes, that is technically correct, but would you consider a circle to be an ellipse with specific attributes, or a shape with different properties (i.e. radius and centre instead of two foci) - would you inherit circle from shape, inherit circle from ellipse, or consider circle to be a special case of ellipse?  Nothing to do with the original topic, but if the OP can follow this discussion then he's on the way to understanding OOP :)

---

### Post by smartbei on 2007-11-21
I might, for the sake of correctness, make circle just a special case of Elipse, since it would use the very same math except with the two foci coincident. However, since many calculations are far simpler for a circle, I would probably define it as a seperate class inheriting from shape. Depends on the circumstance. If I am trying to teach OOP/OOD and want to show how writing the code twice is terrible (even at the cost of efficiency)...

BTW guys- read the OP. He did not edit his post and he specifically said:
> 
This is for python :)


EDIT: changed first paragraph after I realized I thought one thing and wrote another.

---

### Post by LaRoza on 2007-11-21
> **aquavitae said:**
> Yes, that is technically correct, but would you consider a circle to be an ellipse with specific attributes, or a shape with different properties (i.e. radius and centre instead of two foci) - would you inherit circle from shape, inherit circle from ellipse, or consider circle to be a special case of ellipse?  Nothing to do with the original topic, but if the OP can follow this discussion then he's on the way to understanding OOP :)

Yes, it was off topic, but it is important to design objects well, and this might come up...

I would (if I were to make a graphing program) not have a circle, but an ellipse, as it is the same thing. If I were to make anothe non-mathematical program, making a circle class might make more sense.

---

### Post by Mr.popo on 2007-11-21
Thank you all for the replies.I will nowi read through them all now and hope they make me undertsnad oop more
thanks.

---

### Post by alek12 on 2008-01-26
Try downloading and running this software:

[www.enterpriseanalyst.net](www.enterpriseanalyst.net)

Read carefuly its help, especially the part about UML (you need it to visualize OO). 
Then install it and try to go through the Step by step tutorial. It will help you make your first moves.
Good luck!

Alek.

---

### Post by hod139 on 2008-01-26
> **alek12 said:**
> Try downloading and running this software:

[www.enterpriseanalyst.net]("http://www.enterpriseanalyst.net")

Read carefuly its help, especially the part about UML (you need it to visualize OO). 
Then install it and try to go through the Step by step tutorial. It will help you make your first moves.
Good luck!

Alek.
Is this spam?  This is your first post and it is to some paid software.  I haven't reported it as spam to give you a chance to reply and explain the post.

---

### Post by jingo811 on 2008-03-18
Having struggled with OOP by following the book PHP Anthology - Harry Fuecks.  I'm starting to suspect that the art form OOP is only intended for _[SIZE="4"]academic programmers[/SIZE]_ and not for most ppl from other walks of life.
I've spent over 6 months trying to refactor an OOP class file into procedural form, I still can't see the relation and modify things like I want to :(
[INDENT]Anyhow enough complaining here's something that might help somebody out if OOP for PHP is the same as OOP for Python and other languages.[/INDENT]


> The big advantage of classes is that they let you define variables and the functions that use them together in one place, while keeping the functions hidden from unrelated code.  This highlights one of the key theoretical point about the object oriented paradigm.

[LIST]
[*]The **procedural **paradigm places most emphasis on **functions**, variables being treated as little more than a place to store data between functions calls.
[*]The **object oriented** paradigm shifts the emphasis to **variables**; the functions "back" the variables and are used to access or modify them.
[/LIST]
[RIGHT][FONT="Courier New"]The PHP Anthology, Vol 1 - page 34, by Harry Fuecks[/RIGHT][/FONT]

---

### Post by themusicwave on 2008-03-18
> **jingo811 said:**
> Having struggled with OOP by following the book PHP Anthology - Harry Fuecks.  I'm starting to suspect that the art form OOP is only intended for _[SIZE="4"]academic programmers[/SIZE]_ and not for most ppl from other walks of life.


I would say OOP is not just for academics.  I am not in college anymore, I am in industry and I use OOP daily.  

OOP is just a different way of thinking of programming.  Sometimes it makes sense, sometimes it doesn't.  For some projects I just use procedural programming, for most I use Objects.

I'm not sure what you define an "Academic programmer" as so I may be one and not know it.  I do have a B.S. in Software Engineering.  However, I am also in industry creating real systems.

---

### Post by guilly on 2008-03-18
> **themusicwave said:**
> I would say OOP is not just for academics.  I am not in college anymore, I am in industry and I use OOP daily.  

OOP is just a different way of thinking of programming.  Sometimes it makes sense, sometimes it doesn't.  For some projects I just use procedural programming, for most I use Objects.

I'm not sure what you define an "Academic programmer" as so I may be one and not know it.  I do have a B.S. in Software Engineering.  However, I am also in industry creating real systems.

I must agree 100%. Theres no way that OOP is only for Academics.

---

### Post by pbpersson on 2008-03-18
I do not know Python so I cannot comment on that aspect of things.  I have done most of my development in VB.NET and this year I hope to graduate up to Java ;) and begin creating some true cross-platform applications.

There are two important aspects of OOP that I did not see in this thread.  One is encapsulation.  For instance, you can create an object called Employee and inside that object, the object knows the properties of an employee and the methods.  Properties might be sex, age, address, state, country, etc.  Methods might be promotion, hire, fire, name change, department move, etc.  The Employee object knows about employees, how to report on and change employees, and how to get at the data.  From the outside you do not know that, you just send it requests.  

The other aspect that was not mentioned is inheritence.  You can create generic classes with properties and methods.  Let us say you create a class called vehicle.  All vehicles have wheels, an engine, doors, windows.  Now when you have all the properties and methods created you create a new class called truck which inherits all the properties and methods from vehicle.  You just change what you need to - trucks are larger, can carry more cargo, etc.  Then under that you might create a new class called 4-Wheel-Drive truck.  You don't have to create the new class from scratch - you just inherit everything from truck and change those attributes that are different - most of the code is already being inherited.

Object Oriented Programming was created because as applications become much more complex, our minds cannot hold all the complexities in there at once.  Using encapsulation you can ignore the details in the lower modules and treat those modules as black boxes.  The concept of classes allows us to re-use a great deal of code without always re-inventing the wheel, so to speak.  :)

---

### Post by jingo811 on 2008-03-18
> **themusicwave said:**
> 
....
....
I'm not sure what you define an "Academic programmer" as so I may be one and not know it.  I do have a B.S. in Software Engineering.  However, I am also in industry creating real systems.

What I mean by "Academic programmer" is a person who have gone through some sort of course in programming design.

People who don't spend time on "blueprint-thinking" before typing their first codes is according to my definition a "non-Academic programmer".  Still this category of programmers might still be skilled at what they do.  But skipping or not having learnt the "blueprint-thinking" before they code is going to make OOP hard to grasp.

Like most people in here talking about:
instance=Lassie
class= Dog
Cars and geometrical shapes have a jigsaw in their head usually gained from taking a theoretical type programmers course.  A jigsaw that me and most newbies will lack which will make grasping OOP weird and illogical.

Seeing somebody teach this kind of "blueprint-thinking" in real life and reading about it is very different.  The message will get messed up when a newbie reads it and interprets it me thinks.  Personally I've given up on learning OOP but then maybe it's b'coz I've always been slow in the head.

---

### Post by themusicwave on 2008-03-18
> **jingo811 said:**
> What I mean by "Academic programmer" is a person who have gone through some sort of course in programming design.

People who don't spend time on "blueprint-thinking" before typing their first codes is according to my definition a "non-Academic programmer".  Still this category of programmers might still be skilled at what they do.  But skipping or not having learnt the "blueprint-thinking" before they code is going to make OOP hard to grasp.

Like most people in here talking about:
instance=Lassie
class= Dog
Cars and geometrical shapes have a jigsaw in their head usually gained from taking a theoretical type programmers course.  A jigsaw that me and most newbies will lack which will make grasping OOP weird and illogical.

Seeing somebody teach this kind of "blueprint-thinking" in real life and reading about it is very different.  The message will get messed up when a newbie reads it and interprets it me thinks.

OOP is hard to grasp at first.  Trust me even the college courses on it are tricky.  Especially when your professor has a think chinese accent and you speak english.

OOP is one of those things where you have a lightbulb moment.  After you trudge through it for awhile one day the light goes off and you say "Aha it all makes sense".  At least thats how my classmates and I experienced it.

At the same time, I believe you can learn OOP without getting a degree.  OOP is a very natural way of thinking about things.  When I look at one of the objects sitting on my desk I tend to think its attributes and what it can do.

My Box of Tissues has the following attributes:  
width
height
depth
thickness
color
brand
quanity of tissues remaining
position(relative to my desk)

We can see this naturally just by looking at the object.  I can also tell there are certain actiosn I could od with this tissue box like:

removeTissue - decrease the quantity of remaining tissues
throwBox - change the postion of the TissueBox, and possibly its hieght, width and depth.

Objects in the real world has attributes or properties and also actions associated with them.

All that OOP is at the very core is finding way to make virtual objects.  This requires thought before you code.  You have to sit down and think about what your program is going to do.  What data it contains and how this data relates.

Try writing out a list of all the data and actions your program needs to have.  Now take that list and group data and actions together where it makes sense.  Give that group a name and you have a Class.  Do that until all the data and actions are wrapped up.  Now you have all your classes.  Now you need to figure out how they interact and define that in your program.

Eventually this process will just sort of happen without any or much conscious effort.

I hope that made sense...

---

### Post by CptPicard on 2008-03-18
> **jingo811 said:**
> 
I've spent over 6 months trying to refactor an OOP class file into procedural form, I still can't see the relation and modify things like I want to :(

I wonder what the problem is you're having there. In theory, transforming a class into procedural form is actually quite simple -- you put the data into some kind of a record (C's struct), and then take all the methods of the class and give each one of them a new parameter that takes the type of that record. So object.method(param) becomes method(object, param). Python does this even in its OO code, by having such an explict "self".

---

### Post by pmasiar on 2008-03-18
OOP is about packing functions together with data they work with, so you don't have to define different functions to work with different types of data (or have universal function with big switch statement inside). It is about having **namespace, where functions and data attributes what belong together are kept together,** and separate from other namespaces. Polymorphism and inheritance are just nice addition (and you can ignore them in the beginning) to the most fundamental encapsulation principle. As such, OOP is very practical and pragmatic - it allows write more maintainable programs, what can be less academic? Since when academics care about maintaining the code?

---

### Post by TreeFinger on 2008-03-18
While learning a little C++ I always wondered what these mysterious 'objects' were in object oriented programming. well this semester my programming class is in Java and not C++.

Now I know what an object is :)

this is quite general.. this is from my professor..

a Class is a data type and an object is a variable of type Class.

---

### Post by fyplinux on 2008-03-18
I think OOP is the natural way of humans communication. you state something, you need a noun, that is semantically equivalent to Class. 

Everything has its own feature, you need to describe them more specifically, that is semantically equivalent to Object.

---

### Post by ruy_lopez on 2008-03-18
OOP is an ontological construct. The difficulty at first is coming to terms with the language. Describing OOP necessitates the use of tautologies. It can seem like nonsense at first. When the English language has many terms in the one sentence all referencing each other, it becomes difficult to understand. But OOP is tautological and self-referential so there's no better way to describe it.

---

### Post by jingo811 on 2008-03-20
> **CptPicard said:**
> I wonder what the problem is you're having there. In theory, transforming a class into procedural form is actually quite simple -- you put the data into some kind of a record (C's struct), and then take all the methods of the class and give each one of them a new parameter that takes the type of that record. So object.method(param) becomes method(object, param). Python does this even in its OO code, by having such an explict "self".

I demonstration perhaps?  The technical terms you used sounded like an important solution to do things, but I need daily-english-vocabulary to understand what you just said regarding the _strategy_ for chopping up my OOP before I can refactor into procedural.

All these a 100 something rows of codes with the references (&) business makes me dizzy and confused before I even get started on refactoring the variables :confused:
_Refactoring this entire OOP class file into procedural might be overkill but what's your strategy when you see this for the first time?  _
How do you chop it up before refactoring?

**MySQL.php**
[PHP]<?php
/**
* @package SPLIB
* @version $Id: MySQL.php,v 1.1 2003/12/12 08:06:07 kevin Exp $
*/
/**
* MySQL Database Connection Class
* @access public
* @package SPLIB
*/
class MySQL {
    /**
    * MySQL server hostname
    * @access private
    * @var string
    */
    var $host;
    /**
    * MySQL username
    * @access private
    * @var string
    */
    var $dbUser;
    /**
    * MySQL user's password
    * @access private
    * @var string
    */
    var $dbPass;
    /**
    * Name of database to use
    * @access private
    * @var string
    */
    var $dbName;
    /**
    * MySQL Resource link identifier stored here
    * @access private
    * @var string
    */
    var $dbConn;
    /**
    * Stores error messages for connection errors
    * @access private
    * @var string
    */
    var $connectError;
    /**
    * MySQL constructor
    * @param string host (MySQL server hostname)
    * @param string dbUser (MySQL User Name)
    * @param string dbPass (MySQL User Password)
    * @param string dbName (Database to select)
    * @access public
    */
    function MySQL ($host,$dbUser,$dbPass,$dbName) {
        $this->host=$host;
        $this->dbUser=$dbUser;
        $this->dbPass=$dbPass;
        $this->dbName=$dbName;
        $this->connectToDb();
    }
    /**
    * Establishes connection to MySQL and selects a database
    * @return void
    * @access private
    */
    function connectToDb () {
        // Make connection to MySQL server
        if (!$this->dbConn = @mysql_connect($this->host,
                                      $this->dbUser,
                                      $this->dbPass)) {
            trigger_error('Could not connect to server');
            $this->connectError=true;
        // Select database
        } else if ( !@mysql_select_db($this->dbName,$this->dbConn) ) {
            trigger_error('Could not select database');
            $this->connectError=true;
        }
    }
    /**
    * Checks for MySQL errors
    * @return boolean
    * @access public
    */
    function isError () {
        if ( $this->connectError )
            return true;
        $error=mysql_error ($this->dbConn);
        if ( empty ($error) )
            return false;
        else
            return true;
    }
    /**
    * Returns an instance of MySQLResult to fetch rows with
    * @param $sql string the database query to run
    * @return MySQLResult
    * @access public
    */
    function & query($sql) {
        if (!$queryResource=mysql_query($sql,$this->dbConn))
            trigger_error ('Query failed: '.mysql_error($this->dbConn).
                           ' SQL: '.$sql);
        return new MySQLResult($this,$queryResource);
    }
}
/**
* MySQLResult Data Fetching Class
* @access public
* @package SPLIB
*/
class MySQLResult {
    /**
    * Instance of MySQL providing database connection
    * @access private
    * @var MySQL
    */
    var $mysql;
    /**
    * Query resource
    * @access private
    * @var resource
    */
    var $query;
    /**
    * MySQLResult constructor
    * @param object mysql   (instance of MySQL class)
    * @param resource query (MySQL query resource)
    * @access public
    */
    function MySQLResult(& $mysql,$query) {
        $this->mysql=& $mysql;
        $this->query=$query;
    }
    /**
    * Fetches a row from the result
    * @return array
    * @access public
    */
    function fetch () {
        if ( $row=mysql_fetch_array($this->query,MYSQL_ASSOC) ) {
            return $row;
        } else if ( $this->size() > 0 ) {
            mysql_data_seek($this->query,0);
            return false;
        } else {
            return false;
        }
    }
    /**
    * Returns the number of rows selected
    * @return int
    * @access public
    */
    function size () {
        return mysql_num_rows($this->query);
    }
    /**
    * Returns the ID of the last row inserted
    * @return int
    * @access public
    */
    function insertID () {
        return mysql_insert_id($this->mysql->dbConn);
    }
    /**
    * Checks for MySQL errors
    * @return boolean
    * @access public
    */
    function isError () {
        return $this->mysql->isError();
    }
}
?>[/PHP]

---

### Post by CptPicard on 2008-03-20
Not too difficult really (this is some kind of general pseudocode) :)

```

struct MySQL {
	String host
	String user
	String pass
	String dbname
	Connection conn
	Error connectError
}


// You call this by first allocating your struct MySQL, passing it as "self"
void constructMySQL(MySQL self, String host, String user, String pass, String dbname) {
	self.host = host
	self.user = user
	self.pass = pass
	self.dbname = dbname
}

// Connects "self" to database
void connectToDB(MySQL self) {
	// here, you simply change "this" to "self" and and fix function calls accordingly to take the "self"
}

boolean isError(MySQL self) {
	// ... like so..:
	if (self.connectError)
		return true;
	//etc... 
}


struct MySQLResult {
	// vars for MySQLResult
}


// MySQLResult constructor
void constructMYSQLResult(MySQLResult self, MySQL mysql, String query) {
//Same as above
}


```

---

### Post by jingo811 on 2008-03-20
I think I found the missing "Academic" piece of puzzle that I was searching for in the beginning.  It has pictures and clicky buttons, too bad the self-test pages doesn't work :( but still very educational I think I'm starting to get this. :)
[http://homepages.north.londonmet.ac.uk/~chalkp/proj/ootutor/sitemap1.html](http://homepages.north.londonmet.ac.uk/~chalkp/proj/ootutor/sitemap1.html)

---

### Post by pmasiar on 2008-03-20
> **jingo811 said:**
>  to understand what you just said regarding the _strategy_ for chopping up my OOP before I can refactor into procedural.


Refactoring into procedural form has quite a lot of cons:
- former "methods" now live in more global namespace (see PHP and it's 5000 global functions), so you prefix method mane with type name or so
-  no inheritance of course
- more self-discipline needed to keep code of related "methods" together
- because object are not opaque anymore, someone might "save time" and access instance's "property" directly. Later, when you need to change data representation, those changes will blow into your face. OOP programming was invented for a reason, and it does produce more maintainable code. It is higher abstraction, but it makes sense (unless you use Java which overdid OO).

---

### Post by CptPicard on 2008-03-20
> **pmasiar said:**
> 
-  no inheritance of course

You can sort of do inheritance in C if you just think of structs that just get additional members tacked on them when you "inherit" from another struct. You can cast a "derived" struct into the type of the "super-struct" because it has less members and in the same order...

But of course I didn't need to tell *you* that, it's just an interesting point.. :)

---

### Post by pmasiar on 2008-03-21
I know, I even found (and IIRC even linked in some answer somewhere) a post about "simulating object design pattern" in C. It was not pretty :-)

---

### Post by Wybiral on 2008-03-21
> **pmasiar said:**
> I know, I even found (and IIRC even linked in some answer somewhere) a post about "simulating object design pattern" in C. It was not pretty :-)

Guido and friends did it when they wrote Python. Pythons object system works something like this:

The base object:
```

struct object {
    object_type *type;
    long reference_count;
};

```

The "type" points to an instance of a struct that looks like this:
```

struct  object_type {
    object *(*__add__)(object *self, object *other);
    ....
};

```

The method function pointers are filled in for that particular type (the "types" are just instances of the "object_type" structure).

Objects can have other fields in the struct as long as they keep the type pointer and the reference count at the top (they can be dereferenced as the base "object" type since most C implementations will maintain the same spacing for those fields). Lots of pointer casting and dereferencing involved.

Then all you have to do is use:
```

object *a = new_int_object(1)
object *b = new_int_object(2);
object *result = a->type->__add__(a, b);

```

Where "new_int_object" allocates a struct that derives from "object" but has an extra field for the integer (this doesn't matter when it's cast back to the "object", as long as it's dereferenced as an int_object in the type function pointers so integer operations can be defined). Of course, with some macros, you can make it look like this:

```

#define TYPE(self) (self)->type
#define ADD(self, other) TYPE(self)->__add__(self, other)

object *a = new_int_object(1)
object *b = new_int_object(2);
object *result = ADD(a, b);

```

Add some inc_reference / dec_reference to manage the reference counting and you've got yourself a CPython-esque object implementation. lol, I feel like I've butchered this explanation... Egh, anyway... It's neat. But it's obviously not practical for programming with (though it may be practical for designing a language with, such as Python).

---

### Post by inksmithy on 2008-03-21
Well done all, you have taken the OPs thread about basic concepts of OO programming and turned it into a highly specialised and completely irrelevant discussion about obscure parts of programming languages which he didn't mention in his original post.
I bet he feels much more confident about what he wanted to achieve now.

---

### Post by LaRoza on 2008-03-21
> **inksmithy said:**
> Well done all, you have taken the OPs thread about basic concepts of OO programming and turned it into a highly specialised and completely irrelevant discussion about obscure parts of programming languages which he didn't mention in his original post.
I bet he feels much more confident about what he wanted to achieve now.

Looking at the last few posts, it is on topic, remarkably so for a thread in this forum.

---

### Post by CptPicard on 2008-03-21
Well, you aren't exactly contributing are you?

At least there is something to be learned from our discussion, hopefully.

---

### Post by Wybiral on 2008-03-21
> **inksmithy said:**
> Well done all, you have taken the OPs thread about basic concepts of OO programming and turned it into a highly specialised and completely irrelevant discussion about obscure parts of programming languages which he didn't mention in his original post.
I bet he feels much more confident about what he wanted to achieve now.

This thread is like three months old... Hopefully the OP got what they needed out of it by now.

---

### Post by pmasiar on 2008-03-21
> **inksmithy said:**
> Well done all, you have taken the OPs thread about basic concepts of OO programming and turned it into a highly specialised and completely irrelevant discussion about obscure parts of programming languages which he didn't mention in his original post.
I bet he feels much more confident about what he wanted to achieve now.

I have no idea how OP feels now, because she was not back. Problem solved I guess (for her).

Rest of thread we talk to each other and learn from each other. I did not know that learning is strictly limited to OP and nobody else, can you post a link to that part of CoC? :-)

---

### Post by LaRoza on 2008-03-21
> **pmasiar said:**
> 
Rest of thread we talk to each other and learn from each other. I did not know that learning is strictly limited to OP and nobody else, can you post a link to that part of CoC? :-)

Apparently, there is:

[quote="CoC"]
4. Forum Threads and Flaming:
[list]
[*]Flaming and condescending messages: Flames are messages that personally attack, call people names, or otherwise harass another forum member (or any person). These, along with any generally condescending posts will be moved or removed at the moderators discretion.

[*]If the thread is flame-bait (appears to be intended to start an argument or is likely to cause an argument rather than enhance discussion), it will be locked or removed without notice. Individual flame-bait may be deleted or edited at the moderators' discretion. Any users who continue to post in this manner or engage in other questionable practices, like trolling (posting in an attempt to engage people in arguments) may be subject to more serious sanctions.

[*]If the thread turns into an argument, it can be locked or removed without notice. Sometimes a moderator may split the thread or delete certain portions in order to keep the discussion going, but that is not always possible.

[*]All threads must be directly addressing the original post. Any attempts to expand the topic, or address other aspects of the subject is banned. Furthermore, anyone caught trying to learn or teach on a thread not dedicated to that, will banned.
[/list]
[/quote]

---

### Post by pmasiar on 2008-03-21
> **LaRoza said:**
> anyone caught trying to learn or teach on a thread not dedicated to that, will banned

oh my, I am toast :-)

Can we at least have icon for thread where learning is not prosecuted? :-)

---

### Post by LaRoza on 2008-03-21
> **pmasiar said:**
> oh my, I am toast :-)

Can we at least have icon for thread where learning is not prosecuted? :-)

I think we all are...

@AnyoneWhoDidn'tCatchIt I added that last point, there is no such rule.

---

### Post by jingo811 on 2008-03-22
> **inksmithy said:**
> Well done all, you have taken the OPs thread about basic concepts of OO programming and turned it into a highly specialised and completely irrelevant discussion about obscure parts of programming languages which he didn't mention in his original post.
I bet he feels much more confident about what he wanted to achieve now.

I'm the 1st hijacker of this thread I found out about this thread from here:
**Sticky:  Programming Talk FAQ's**
bapoumba 

**Learning Programming/Computer Science** - Please explain OOP
[http://ubuntuforums.org/showthread.php?t=606009](http://ubuntuforums.org/showthread.php?t=606009)

So I think this thread serves a higher purpose than simply help the original poster out.  Besides I think she has made a new thread for her problems so no harm done :)

---

### Post by jingo811 on 2008-03-22
Sorry for the doubleposting but I wanted a clear division from this and the previous matter.  
_Qustion 1._
I have a question regarding constructor.
Why isn't these variables....
```
    var $dbConn;
    var $connectError;
```
....made into these in the constructor section?
```
        $this->dbConn=$dbConn;
        $this->connectError=$connectError;
```
Would adding those into the constructor section create unintentional effects?

_Qustion 2._
The other question is about references (&) is this used on all OOP languages or is it just something specific for PHP?

==================================================================================================
**MySQL.php (excerpt) - class file**
[PHP]<?php
* MySQL Database Connection Class

class MySQL {
    var $host;
    var $dbUser;
    var $dbPass;
    var $dbName;
    var $dbConn;
    var $connectError;


    * MySQL constructor

    function MySQL ($host,$dbUser,$dbPass,$dbName) {
        $this->host=$host;
        $this->dbUser=$dbUser;
        $this->dbPass=$dbPass;
        $this->dbName=$dbName;
        $this->connectToDb();
    }


    * Establishes connection to MySQL and selects a database

    function connectToDb () {
        // Make connection to MySQL server
        if (!$this->dbConn = @mysql_connect($this->host,
                                      $this->dbUser,
                                      $this->dbPass)) {
            trigger_error('Could not connect to server');
            $this->connectError=true;
        // Select database
        } else if ( !@mysql_select_db($this->dbName,$this->dbConn) ) {
            trigger_error('Could not select database');
            $this->connectError=true;
        }
    }


    * Checks for MySQL errors
    function isError () {
        if ( $this->connectError )
            return true;
        $error=mysql_error ($this->dbConn);
        if ( empty ($error) )
            return false;
        else
            return true;
    }

......
......
......
......

}
?> [/PHP]

**Calling_the_class_file.php (excerpt) - index file**
[PHP]
// Connect to MySQL
$dbConn = &connectToDb($host, $dbUser, $dbPass, $dbName);

// A query to select all articles
$sql = "SELECT * FROM articles ORDER BY title";

// Run the query, identifying the connection
$queryResource = mysql_query($sql, $dbConn);

// Fetch rows from MySQL one at a time
while ($row = mysql_fetch_array($queryResource, MYSQL_ASSOC)) {
   echo 'Title: ' . $row['title'] . '<br />';
   echo 'Author: ' . $row['author'] . '<br />';
   echo 'Body: ' . $row['body'] . '<br />';
}


[/PHP]

---

### Post by LaRoza on 2008-03-23
> **jingo811 said:**
> 
Would adding those into the constructor section create unintentional effects?

_Qustion 2._
The other question is about references (&) is this used on all OOP languages or is it just something specific for PHP?

They don't fit in the constructor from what I see. Each function should do one thing, otherwise, it is [One Responsibility Rule]("http://c2.com/cgi/wiki?OneResponsibilityRule")

(Yes, pmasiar, I haven't yet left that site :-))

PHP is a weird language for this study. It wasn't designed as OO from the beginning, and is really high level. References are usually found in most languages that copy by value.

Copy by value:

[php]
function swap(x,y)
{
    temp = x;
    x = y;
    y = temp;
    return;
}
[/php]

In the above function, the **values** of x and y are passed into the function, and the scope of the local variables x and y (the ones in the function) are just copies of them. After the function returns, the variables go out of scope, and the original variables are still the same.

Most languages that I see do this, and usually have some way of passing by reference. 

(Some languages, like Fortran pass by reference all the time, and it makes coding fun.)

---

### Post by jingo811 on 2008-03-23
> **LaRoza said:**
> They don't fit in the constructor from what I see. Each function should do one thing, otherwise, it is [One Responsibility Rule]("http://c2.com/cgi/wiki?OneResponsibilityRule")

_Qustion 1._
I didn't really understand the explanation from that link.  So I try to rephrase my question.  In the book it says a constructor is like a method (internal class function).  
[LIST]
[*]So if they are both regarded as functions what makes a constructor different from a real function in the same class file?
[*]Also what's the purpose with the constructor?
[*]How can I see that a certain variable doesn't belong in the constructor statement?
[*]Also if I don't put in those 2 variables that were intentionally left out how can the calling *.php file see those variables if they are not setup in the constructor like the rest of the variables?
[/LIST]

---

### Post by LaRoza on 2008-03-23
> **jingo811 said:**
> _Qustion 1._
I didn't really understand the explanation from that link.  So I try to rephrase my question.  In the book it says a constructor is like a method (internal class function).  
[LIST]
[*]So if they are both regarded as functions what makes a constructor different from a real function in the same class file?
[*]Also what's the purpose with the constructor?
[*]How can I see that a certain variable doesn't belong in the constructor statement?
[/LIST]

A constructor is a method.

0. A constructor is called when an object is made.
1. To make setting up the object easier.
2. If it doesn't need to be set when an object is made, you don't need it in the contructor

Here is an example:

[php]
class Human
{
    function __construct($sex,$dateOfConception);
    function setHairLength($length);
    function eat($food);
    function __destruct();
}
[/php]

In the above example, I have three functions. One, the constructor, which takes the sex and data of conception of the human. These variables are set when a human is created (Don't go there, I know about reassignment, but ignore that) If you were to make a human, you would want to give the sex and date of conception when it was made.

```

$me = new Human("bot","1988);
$me->setHairLength("Long");

```

See? Now, other methods, for this, eat(), take a value that isn't set when I am made. 

__destruct() is the destructor, which is called when an instance of a class is destroyed, either by the GC or manually.

---

### Post by jingo811 on 2008-03-23
_Questions 1._
[LIST]
[*]I'm getting closer to understanding but there's still one thing that I'm not clear on.  In the book example the constructor included 1 function in its statement **"connectToDB()"** how do I know what function to include in your constructor example?
[*]And the constructor variables what would they be in your example if I wanted to make it look like my php example code?

[*]Would **$sex** and **$dateOfConception** be the only variables made into this format
```
$this->sex=$sex;
$this->dateOfConception=$dateOfConception;
```
[/LIST]


```

<?php

class MySQL {
    var $host;
    var $dbUser;
    var $dbPass;
    var $dbName;
    var $dbConn;
    var $connectError;


 // MySQL constructor

    function __MySQL ($host,$dbUser,$dbPass,$dbName) {
        $this->host=$host;
        $this->dbUser=$dbUser;
        $this->dbPass=$dbPass;
        $this->dbName=$dbName;
[COLOR="Red"]        $this->connectToDb();[/COLOR]
    }
    **function connectToDb ($dbConn)**
    function isError ($connectError)

}
?>

```

```

class Human
{
[COLOR="Red"]    var $sex;
    var $dateOfConception;
    var $length;
    var $food;[/COLOR]

 // Human constructor

    function __construct($sex,$dateOfConception) {
[COLOR="Red"]        $this->???=$???;
        $this->???=$???;[/COLOR]
**        $this->How_do_I_know_what_functions_needs_to_be_included_here?**
    }
    function setHairLength($length);
    function eat($food);
    function __destruct();
} 

```

[LIST]
[*]Also if I don't put in those 2 variables that were intentionally left out from my PHP constructor example 
```
    var $dbConn;
    var $connectError;
```
how can the calling *.php file see/access those variables if they are not setup in the constructor like the rest of the variables?
[/LIST]

---

### Post by LaRoza on 2008-03-23
0. It isn't being included, it is being called. That means that the constructor is calling another function. 
1. If it makes sense to call a function immediately, you put can call it in the constructor
2. Yes.

Functions are supposed to do one thing only. The use of the function in the constructor is showing that that function is doing something which makes sense to have another function created. 

I am in the middle of writing a program now (in C, but it doesn't matter), and one of my functions is doing something that takes a bunch of lines. That code is just cluttering up that function. Eventually, I will move it all into another function and call it to clean up my code.

Here I have to show something shameful...I use PHP for my webpages, but due to my host not having PHP5, I didn't take time to learn PHP5 to the extant that I should have. The OO features of it are not my strong point.

---

### Post by CptPicard on 2008-03-23
You know "what should be in the constructor" by deciding on what needs to be done after memory allocation when creating the object so that the object is, after the execution of the constructor, left in a *sane initial state*.

If you have some object that references other objects and makes use of them, for example, and you don't properly initialize those objects in your constructor, thereby causing errors further down the line, your constructor did not do its job.

A lot of objects do provide convenience constructors however that do more than the minimum required, but that is at the programmer's discretion.

---

### Post by jingo811 on 2008-03-23
```
<?php

class MySQL {
    var $host;
    var $dbUser;
    var $dbPass;
    var $dbName;
    var $dbConn;
    var $connectError;


// MySQL constructor

    function __MySQL ($host,$dbUser,$dbPass,$dbName) {
        $this->host=$host;
        $this->dbUser=$dbUser;
        $this->dbPass=$dbPass;
        $this->dbName=$dbName;
[COLOR="Red"]// If I REMOVE this function will things still work?        $this->connectToDb();[/COLOR]
    }
    function connectToDb ($dbConn)
    function isError ($connectError)

}
?>
```

I'm still unsure about how to deal with constructors.  I've seen more CLASS file examples from that book and most of them just lists the "$this->variables" and then closes the constructor.

While some other CLASS files doesn't even list the "$this->variables" at all and just go directly to some complicated IF / ELSE procedure with some "$this->variables" integrated into the mess.



I guess I'm just looking for a _consistent_ way to do things with the constructor because all  these alternatives is creating a mess in my head and I didn't fully understand what CptPicard meant :confused: Like would my MySQL class file still work if I removed the [COLOR="Red"]$this->connectToDb();[/COLOR] function?

---

### Post by slavik on 2008-03-23
When you allocate the memory for your class, should anything be done with it?
What goes into the constructor is entirely up to the programmer and the situation he/she is in.
There is no consistency of what should go into the constructor.

for example:
```

class A {
   var x;
   var y;
}
```

When you create an instant of the class, what should x and y be? Should they have default (initial) values? Should anything else be done?

The constructor is a fancy way to call an initialization function.

---

### Post by CptPicard on 2008-03-23
> **jingo811 said:**
> I guess I'm just looking for a _consistent_ way to do things with the constructor

As slavik said... it is your job, as the programmer, to make sure you make good use of the constructor. Sure, you can do nothing in it if you want to, but you may have objects around that aren't much good for anything, and then you must do all sorts of initialization elsewhere. So better put that inside the constructor...

---

### Post by mssever on 2008-03-23
PHP is a difficult language to learn OOP in. I'd recommend taking a serious look at Ruby. My experience was that once I begin using Ruby, a purely OO language, OO began to make a lot more sense.

Of course, if you learn Ruby, you might find yourself no longer likeing PHP...

---

### Post by jingo811 on 2008-03-23
I'm being held hostage by PHP so much money and time invested in it.  Besides I've decided to only learn PHP and C well during my lifetime so no more distractions for me tnx :)

I'm getting a feeling that my study material is lacking important information regarding how to build proper Classes from old Procedural codes.  At least it's presenting so much info at once it confuses more than teaches.  How did you guys learn OOP do you have any recommended links or books for building Classes and Objects.  Best would be if you have some PHP related study material.

---

### Post by LaRoza on 2008-03-23
> **mssever said:**
> PHP is a difficult language to learn OOP in. I'd recommend taking a serious look at Ruby. My experience was that once I begin using Ruby, a purely OO language, OO began to make a lot more sense.


Same with Python. PHP is not the best language with which to learn OO, I agree with that.

---

### Post by slavik on 2008-03-23
another thing is too look at OOP as convenience rather than a necessity ...

---

### Post by jingo811 on 2008-03-23
> **slavik said:**
> another thing is too look at OOP as convenience rather than a necessity ...

Yup and it seems like using OOP makes the execution time over 200% slower compared to using Functions in Procedural programming.
[http://www.webmasterstop.com/56.html](http://www.webmasterstop.com/56.html)

But I force myself to get PHP OOP so I can tap into the chest of gold (PEAR) containing codes already made by expert programmers in relation to myself.
Knowing how to build a Class file makes it easier to modify other peoples work so far no luck.

---

### Post by mssever on 2008-03-24
> **LaRoza said:**
> Same with Python. PHP is not the best language with which to learn OO, I agree with that.
Actually, I think that Ruby is better than Python as far as OOP goes. Python is a mixture of procedural and OOP. (For example, len(), str(), etc. are procedural.) Python handles OOP fine, but my experience was that Ruby helped me to make sense of OOP because *everything* is OO. Now, Ruby has a fair amount of syntax sugar that can hide the OO, and you can write procedural code in Ruby if you want, but under the hood, it's pure OO.

(Don't take this as a criticism of Python; I just think that Ruby provides a better demonstration of OO. After all, Ruby is descended from the original OO language, Smalltalk.)

---

### Post by pmasiar on 2008-03-24
> **mssever said:**
> Python is a mixture of procedural and OOP. (For example, len(), str(), etc. are procedural.) 

There is another approach to that: len(), str() might be considered **generic functions**, which work for any argument (making use of dynamic typing).


> (Don't take this as a criticism of Python; I just think that Ruby provides a better demonstration of OO. After all, Ruby is descended from the original OO language, Smalltalk.)

I agree that Ruby is more "pure OO", but it's syntax is also too close to Perl, IMHO. It is fine if you hack Ruby daily, but if you don't touch Ruby for couple months and then come back, I am afraid there will be gaps like with Perl: forgetting "cool" trick. Python is more straightforward in this sense, not trying to be clever. Nothing against Ruby, it is matter of taste I guess. Maybe that is why many hackers who did not get burned by Perl do like Ruby, and scientists who code only occasionally prefer Python (as more obvious of the two).

---

### Post by LaRoza on 2008-03-24
> **mssever said:**
> Actually, I think that Ruby is better than Python as far as OOP goes. Python is a mixture of procedural and OOP. (For example, len(), str(), etc. are procedural.) Python handles OOP fine, but my experience was that Ruby helped me to make sense of OOP because *everything* is OO. Now, Ruby has a fair amount of syntax sugar that can hide the OO, and you can write procedural code in Ruby if you want, but under the hood, it's pure OO.

(Don't take this as a criticism of Python; I just think that Ruby provides a better demonstration of OO. After all, Ruby is descended from the original OO language, Smalltalk.)

I like a language that mixes paradigms :-)

I guess it is personal preference. Ruby isn't really all that different from Python or even Perl.

---

### Post by Wybiral on 2008-03-24
> **mssever said:**
> Actually, I think that Ruby is better than Python as far as OOP goes. Python is a mixture of procedural and OOP. (For example, len(), str(), etc. are procedural.)

Actually, in Python len, str, int, float... None of those builtin functions are really procedural. When you write "int(string)" in Python, while int() is still a function, it's actually calling "string.__int__()". It's just a convention to make objects more generic (it enforces the use of the generic methods so that each object doesn't have a different method for returning an int, for instance). As pmasiar said, it's called "duck typing" (strings have a method that returns an int, so they quack like a duck... Just like floats).

---

### Post by The Cog on 2008-03-24
You guys might find this paper interesting. It's about teaching OO programming concepts using paper cards with opject functions written on them. I happened across it a couple of years ago.
[http://c2.com/doc/oopsla89/paper.html](http://c2.com/doc/oopsla89/paper.html)

---

### Post by jingo811 on 2008-03-24
My initial goal before learning basic PHP OOP was to be able to refactor a login system I bought, from Procedural Functions layout into OOP.
Now that I'm a bit wiser than 2 weeks ago :) and looking at this login system divided neatly into circa 9 files and 3 folders with a whole lot of includes in between them.  Which will make portability a pain but....

I realise that transforming it into OOP will make it even harder to comprehend and manage.  And then there's the excuse with OOP running 200% slower than Procedural Functions so now I'm dropping of this OOP train for good.

Next stop some Database experiments and then read the K & R book in C programming.  Then hop onto the WineHQ train.

---

### Post by twothird on 2008-04-05
am I not getting something..? everyone is comparing PHP and RoR and there's nothing about ASP.Net, and that's THE OO framework.. is that because it's microsoft? I'm going with the money :)

---

### Post by pmasiar on 2008-04-05
How you determined the "the" in OO frameworks? :-)

Web app framework and OO framework are diffeent animals. And I wrestled with ASP.NET (in VB no less!)  for a while, and the incredible sucking sound is still with me. Are you familiar with any other web app framework except ASP.NET, and some other non-MSFT languages?

I prefer to go with productivity of my tools :-)

---

### Post by pavel989 on 2008-07-18
Dunno the exact story, but thought yall would find it interesting. My mom's a programmer, more of a web programmer, but word gets around about stuff in the workplace.

neways

OOP apperently was developed by some company (ill get back to you with the name) or maybe it was mainstreamed by it, but what they did, is like for example, they'd name methods based on what the goal was, simply so that they could all understand what other were talking about.

and they'd put em on cards wif magnets, and move 'em around on a white board, taking notes, puttin them in order which seemed most effecient.

(I could be way off, im try to get the full story and verify soon enof)

---

### Post by jingo811 on 2008-08-12
> **twothird said:**
> am I not getting something..? **everyone is comparing PHP and RoR and there's nothing about ASP.Net**, and that's THE OO framework.. is that because it's microsoft? I'm going with the money :)

OOP is a concept that's not restricted to any certain language.  The reason why people have been using PHP and RoR references so far, is probably because that's the languages people know.  If you know OOP using ASP then just shoot.

You got some valuable OOP tips using ASP then share because OOP works in many languages anyways.  People are smart they can adapt.


**Offtopic:**
Here's a nice OOP video tutorial.  If only all teachers in the world could've had his teaching philosophy then life would be so much easier.
[http://www.killerphp.com/videos/object-oriented-php-videos.php](http://www.killerphp.com/videos/object-oriented-php-videos.php)

---

