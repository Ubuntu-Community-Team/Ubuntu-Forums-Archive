---
title: "OOP Application Topology"
date: 2010-08-30
forum: Programming Talk
---

### Post by yknivag on 2010-08-30
I've been programming for several years now, but only ever in procedural languages, but in an attempt to get a little more up-to-date I'd like to try my hand at some OOP.

I think I've got my head around the basics of objects having properties and methods etc, and I've played around with lots of examples but whilst I can work our how other peoples' code is working defining the topology for my own project is defeating me.

Here's the basics, it's a web-based application and will be developed in PHP as that's what I'm most comfortable using.  The purpose is to provide a diary and ticketing function for a theatre.  So there are several 'classes' of object: "production", "performance", "ticket", "customer" etc.

A production can have many performances and obviously a performance can have many tickets. But a ticket is only for one performance of a production.

This is where I'm confused: obviously each of these three classes has unique properties, but each is dependant on one further up.  So do I use three independent classes? eg

[PHP]class production {

   public title;
   public playwright;
   public director;
   public company;
}

class performance {

   public date;
   public venue;
}

class ticket {

   public seating_area;
   public price;
}[/PHP]

Or something like this...

[PHP]class production {

   public title;
   public playwright;
   public director;
   public company;
}

class performance extends production {

   public date;
   public venue;
}

class ticket extends performance {

   public seating_area;
   public seat_number;
   public price;
}[/PHP]

The latter seems the most logical, but the former seems more "correct" as a ticket isn't a "type" of performance and a performance isn't a "type" of production.  But obviously what we're selling is a ticket which needs to contain information about the performance it's for and the production too.

Both would work, but which is more correct?  Or have I got this all wrong completely?

---

### Post by NovaAesa on 2010-08-30
I think you would be better off with the first example you gave, however you would have to add pointers or references to the objects "above" each class.

Actually, this sort of problem seems to be much more suited towards a relational database system.

---

### Post by hanniph on 2010-08-30
Latter example is definitely wrong. Inheritance models 'is-a' relationship so according to your code we could say that performance is production and ticket is both performance and production. It just doesn't make any sense. 

The former example is clean and correct but classes don't have any informations about other classes, so they are not complete. 

To add requireed information you could model 'has-a' relationship. For example Ticket needs to know to what performance it belongs to and performance needs to be associated with production, so you could have:
[PHP]
class production {

   public title;
   public playwright;
   public director;
   public company;
}

class performance {

   public date;
   public venue;

   // reference to production 
   public production;
}

class ticket {

   public seating_area;
   public price;
  
  // reference to performance
  public performance;
}  
[/PHP]

If you need to know about performances given a production object, you could store array of performance references inside a production object. My main point here is that inheritance is not a solution for this situation.

---

### Post by Vaphell on 2010-08-30
+1 to first, also with references

if you know anything about relational databases then it's very similar

i'd do something like this
production ( ..., ref_to_performance_list )
performance ( ..., ref_to_production, ref_to_ticket_pool )
ticket ( ..., ref_to_performance )

that way you can get to any data while being wherever, without data redundancy in objects

---

### Post by yknivag on 2010-09-01
Hi everyone, thanks for the replies -they make things much clearer.

> **NovaAesa said:**
> Actually, this sort of problem seems to be much more suited towards a relational database system.

The data itself is stored in a relational database, but I wanted a better way of handling it in the application layer, than the way I do currently which is to continually refer back to the database.  Plus I wanted an excuse to learn some OOP techniques as I've never done it before.

At the moment, everything is procedure driven, I'm hoping if I can abstract all the functionality to classes and methods I'll be able to expand it with a "plug-in" style approach.  Then with some help from [Smarty]("http://www.smarty.net/") morph it into a proper 3-tier project.

I'm sure I'll be back with more questions as I get stuck into trying to turn theory into practice...

---

### Post by yknivag on 2010-09-01
> **hanniph said:**
> [PHP]
class production {

   public title;
   public playwright;
   public director;
   public company;
}

class performance {

   public date;
   public venue;

   // reference to production 
   public production;
}

class ticket {

   public seating_area;
   public price;
  
  // reference to performance
  public performance;
}  
[/PHP]

Hi hanniph, I like this structure as it resembles very much what I have at the moment in terms of the database.  My only question would be how would I then refer to the properties of the referenced objects?  IE when a customer buys a ticket then:
[PHP]$myTicket.display();[/PHP] should show them details of the associated production and performance as well as of the ticket.

Would it be easier to have the performance object as a property of the ticket object, and similarly the production object as a property of the production one?  Or would it be much easier (as customers only ever buy a ticket) to simply have one class for ticket which would contain all the associated information?

Apologies for the newbish questions.  Despite having programmed extensively for a couple of decades I've never touched OOP and coming from a procedural background seems much harder than coming in cold with nothing to "un-learn".

---

### Post by hanniph on 2010-09-01
> **yknivag said:**
> 
Would it be easier to have the performance object as a property of the ticket object, and similarly the production object as a property of the production one?  Or would it be much easier (as customers only ever buy a ticket) to simply have one class for ticket which would contain all the associated information?


IMHO, one big class that encapsulates all of the domain details is a big "no no". Putting all the information inside one class doesn't differ much from procedural approach, where you have one all your functions in one file. One of the ideas of OOP is to have bunch of objects talking to each other, so the proper way would be to model separate entities into different classes. What's more, having clear separation of concerns seems cleaner and it would easier to update your code if the application needed to grow. 

Plus, it's easy to access the properties of encapsulated objects. For example:
[PHP]
class Ticket {
 ...
 
 function display(){
  echo $this->price . '$, ' . $this->performance->production->title; 
 }
}
[/PHP]

---

### Post by phrostbyte on 2010-09-01
You can usually persist objects directly into a database. The kind of thing is managed by ORMs (object-relational mappers).

---

### Post by yknivag on 2010-09-05
> **hanniph said:**
> IMHO, one big class that encapsulates all of the domain details is a big "no no". Putting all the information inside one class doesn't differ much from procedural approach, where you have one all your functions in one file.

I've spent far too long programming in a procedural way.  I clearly have a lot to un-learn!  Again thanks for your patience and help - it really is appreciated.

> **hanniph said:**
> One of the ideas of OOP is to have bunch of objects talking to each other, so the proper way would be to model separate entities into different classes. What's more, having clear separation of concerns seems cleaner and it would easier to update your code if the application needed to grow. 

Plus, it's easy to access the properties of encapsulated objects. For example:
[PHP]
class Ticket {
 ...
 
 function display(){
  echo $this->price . '$, ' . $this->performance->production->title; 
 }
}
[/PHP]

This is exactly where I want to get to.  All I need to know now is how to define these inter-linked classes and how when I say tell the app that the $myTicket object refers to tbl_tickets.TicketID in the database that I can automatically populate the performance and production details also.

I'm guessing it needs to be something like this:
[PHP]
class Ticket {
	public $ticketID;
	public $performanceID;
	...									//etc until all properties are defined

	private $_performance; //encapsulated object

	public function __contsruct($ticketID = "") {
		if($ticketID == "") {
			//this is a new ticket being created we'll need to define everything.
		}
		else {
			//this is a defined ticket being looked at or sold
			//code to retrieve ticket details from database
			if($this->_performance == null && $this->performanceID != "") {
				$this->_performance = new Performance($this->performanceID);
			}
		}
	}

	public function display() {
		echo "Ticket for ".$this->_performance->_production->name." on ".$this->_performance->date.". Cost £".$this->price.".";
	}
}

class Performance {
	public $performanceID;
	public $productionID;
	...									//etc until all properties are defined

	private $_production; //encapsulated object

	public function __contsruct($performanceID = "") {
		if($performanceID == "") {
			//this is a new performance being created we'll need to define everything.
		}
		else {
			//this is a defined performance.
			//code to retrieve production details from database
			if($this->_production == null && $this->productionID != "") {
				$this->_production = new Production($this->productionID);
			}
		}
	}
}

class Production {
	public $productionID;
	...									//etc until all properties are defined

	public function __contsruct($productionID = "") {
		if($productionID == "") {
			//this is a new ticket being created we'll need to define everything.
		}
		else {
			//this is a defined performance.
		}
	}
}

//If I want to display a particular ticket detail then I should be able to...

$myTicket = new Ticket("456");
$myTicket.display();
[/PHP]

Of course I may be completely off track again!

---

### Post by Vaphell on 2010-09-05
i'd say that you get the idea though i don't think that performance and ticket should even have a parameter-less constructor. Of course it doesn't matter because it's an academic example but in general in real life scenarios i think it doesn't make much sense to call production and performance constructors because you create a ticket :)
Also productionId in Performance is superficial because you can simply reach to the referenced object and test it there, if for whatever reason that reference was to be changed you'd have to make sure that the variable is also updated. That's why it's best to keep only 1 copy of the data that links objects logically together.

imo the workflow should go like that:
prod = new Production( ... )
perf = prod.newPerformance( ... ) //performance constr is buried here and it's in the production's context right off the bat
ticket = perf.newTicket( ... ) //ticket constructor buried here, same story
of course it's totally interchangeable with new Ticket( perf_ref or perf_id ) but for whatever reason i think that's more elegant way.

i don't consider myself a programmer so take these with a not so tiny grain of salt :-)

---

### Post by yknivag on 2010-09-05
Hi Vaphell, thanks for your input.  You've made me think about this from a different angle.

> **Vaphell said:**
> imo the workflow should go like that:
prod = new Production( ... )
perf = prod.newPerformance( ... ) //performance constr is buried here and it's in the production's context right off the bat
ticket = perf.newTicket( ... ) //ticket constructor buried here, same story
of course it's totally interchangeable with new Ticket( perf_ref or perf_id ) but for whatever reason i think that's more elegant way.

i don't consider myself a programmer so take these with a not so tiny grain of salt :-)

That workflow is all well and good from the perspective of adding stuff in from the boxoffice users.  However, the customer wants to buy a ticket not a production, thus they need a basket object to which they add ticket objects.  Each ticket however belongs to a particular performance of a particular production and such must reference each.  It creates each because it needs to be able to refer to properties of those objects.

In "real-life" it's easy:

ONE production has MANY performances each of which have MANY tickets. The database design reflects this simplicity.  However, trying to create classes in php to resemble this is something different!

I think I need to start this OOP adventure with something much simpler!  As I'm really struggling to see how this will work as the user goes from page to page, as I understand it, there needs to be some way to persist these objects in memory otherwise they have to be redefined en-block every time a user loads a new page of the application, whether or not the customer is going to actually do anything with them.

---

### Post by Vaphell on 2010-09-05
nah, this production/performance/ticket is a very good example, because there are only few classes and you want to get familiar with the idea.


and you are right that my idea was not so perfect for ticket sales. And i now understand what you meant by //all the details go here. I erroneously assumed that you wanted to allow creation of prod/perf from the ticket but i think you simply wanted something along the lines of 'there is a combobox 'pick your performance' and use that choice to create the relation.

> ONE production has MANY performances each of which have MANY tickets. The database design reflects this simplicity. However, trying to create classes in php to resemble this is something different!

it's really not that different.
'normal' database row = single object, data columns = object variables
1-to-many relation = object being a list of 'many' objects.
I even mentioned it in my first post that perf should have a ref to the ticket pool (list of tickets) and production should have a list of planned performances attached.
With that the structure of objects is 100% compatible with the database logic.

be warned that i know nothing about php, i speak in general from my 0 market value experience with the custom in-house OOP language with database backend :-)

---

