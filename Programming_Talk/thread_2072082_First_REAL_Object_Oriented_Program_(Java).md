---
title: "First REAL Object Oriented Program (Java)"
date: 2012-10-17
forum: Programming Talk
---

### Post by kevinharper on 2012-10-17
I have been reading A LOT about true OOP and how it differs from procedural programming. I get the difference. I'm ready! A few days ago [I posted a GUI]("http://ubuntuforums.org/showthread.php?t=2070879") for a CSV reader I am making.

Here are classes that I have come up with:
```
Start:
   displays GUI

GUI:
   adds top
   add content
   add bottom
      to JFrame

Top:
   contains
      Open JButton
      Save JButton
      Search functionality

Open:
   FileChooser GUI (directory browser) to select file
   DataParser();
   CreateRecord();
   Pass Results to Content class

Save:
   GUI (directory browser) to select destination folder
   Prevent User from saving file named like another existing file

Search:
   contains JField and Save JButton; conducts search
   passes search result string to Content

Content:
   data JTable if opening csv file
   SearchReults JTable if user has conducted a search

Bottom:
   NumResults()
   PageResults()

Utility Class:
   random functions that do not belong in any of the object mentioned above
```

Can anyone think of any other essential classes? Can anyone think of a reason I may not need a class/object I've listed?

---

### Post by muteXe on 2012-10-17
As a rough guide (not always true though) i tend to use nouns for classes, and verbs for methods in those classes.

So a class called 'open' doesnt really fit into how i'd write it. not saying it's wrong though.

What i sometimes do is write a quick paragraph about what the whole thing should do, then go back and underline all of the nouns in the paragraph. That might give you a starting point for some of your classes.

---

### Post by ofnuts on 2012-10-17
You should have a look at the [Model-View-Controller]("http://en.wikipedia.org/wiki/Model-view-controller") design pattern.

---

### Post by kevinharper on 2012-10-17
MuteXe: Thank you! I will do that. Sounds like a good idea.

ofnuts: That's actually what I was going for. The user doesn't interact w/ the information. He/She clicks a button that in turn tell an object to do its thing. Is there a flaw in how I'm having these objects communicate with one another?

---

### Post by trent.josephsen on 2012-10-17
To me, this design looks a bit... *complex* for a first design with no code written. Not that 9 classes is too much, but you're still in the design stage and I think you're delving too deeply into the details without working out the high-level design. Think about it: is there no way to express what this program will do without describing 9 different elements?

When you're out to build an airplane, you don't say "Well, I'm going to need some wings, and an engine, and some seats inside, and some windows, and landing gear" -- you start by looking at the *systems* that make up an airplane, and interpolate from there into the implementation details. Same with any kind of design, really.

I guess what I'm saying is, first break your program down into a few classes (let's say 3), and then think about what code will go into which class, and how you might need to split those 3 classes to keep them short and focused. Model-View-Controller might be a good place to start with that.

---

### Post by 1clue on 2012-10-17
The problem is that you're still haphazard in how you're picking your objects.

I referenced MVC in another thread with you, I would strongly recommend you follow the link in the earlier post on this thread for reference.

While you could do it the way you're describing and make it work, your code will be difficult to maintain in a real-world environment, and could become very difficult to keep your business logic from infecting your UI.

Are you learning this in a class or are you trying it on your own?  You should be learning a test first strategy.  [http://www.extremeprogramming.org/rules/testfirst.html](http://www.extremeprogramming.org/rules/testfirst.html)

There are things that test-first does for you:
[LIST=1]
[*]It makes you define the purpose for what you're writing.
[*]It keeps you on track so you write the simplest possible code which accomplishes that purpose
[*]If it can be tested as a single piece then it's easier to remove and replace that piece later with little effort.
[*]It changes the focus of your efforts subtly, to make you think of overall strategy.  You wind up with less spaghetti and more interacting objects.
[*]It lets you know when you're done.
[/LIST]

I've been a professional programmer for decades.  We only relatively recently learned about test-first, and frankly that's one of the last things we as a company adopted because none of us thought it would be very helpful, we all thought it would be a monumental waste of time.

It turns out we were exactly wrong.  Writing a test for existing code is the easiest code review you can get.  If you can't write a test for what you already have, then chances are there's a design problem with the code, even if you don't know why.  It took us a few years on some of our legacy code, but now we know what's wrong, why it's wrong and have replaced the most egregious examples or scheduled them for replacement.  In one case we took an entire legacy application which was untestable and scrapped it.  We rewrote the entire thing because that would take less effort than writing the tests for it.

For new code, test-first is easy and natural.  Think of the test code as your customer contract.  You're making a widget?  What's it supposed to do?  You need to develop a list of use cases, starting with what is given as input and what should happen with that input.  So each verb (method) gets tested with at least one use case (test) and possibly more.  Write it all down in comments in your test class right away, and then slowly write tests that accomplish the things in your test class.  If the new code causes your old tests to pass, you can more easily find out why.

---

### Post by Intrepid Ibex on 2012-10-17
[Wrong thread].

---

### Post by ofnuts on 2012-10-17
> **kevinharper said:**
> 

ofnuts: That's actually what I was going for. The user doesn't interact w/ the information. He/She clicks a button that in turn tell an object to do its thing. Is there a flaw in how I'm having these objects communicate with one another?

Too many classes IMHO. I don't see much purpose in having specific classes for actions such as Load/Save/Search... these should be methods in the controller in the MVC paradigm. You are also exposing too much the classes in your UI. These tend to be rather pragmatic (one class for a JPanel and its contents, for instance). The controller should only talk to the top UI class, which is the one who knows where & how things are displayed.

---

### Post by 1clue on 2012-10-17
Your UI classes should not have significant code for application function.  Code here should be limited to that necessary to display the UI, populate data in the UI and pull data from the UI to pass back to the business logic.

Likewise, similar function is usually put into a single class.

Your screen certainly has a bunch of objects in it, but those objects are usually a prefabricated class you're using.  A button, a grid, etc.  Note that those widget classes don't actually have business logic, they only have enough code to make the widget work.

If you put extra code in those classes then they're no longer a general purpose class, they're only useful in the exact situation you designed.  Likewise you now have to look over your entire code base to get to the business logic.

Again, we get to MVC design.  The buttons and windows are all the view layer.  You should be able to completely delete the view and controller and add another one, and the business logic stays.  Better yet, you should be able to complete your Java swing UI app, then add an additional web layer and have both have exactly the same business logic, the same classes used at the same time.

As a use case scenario, let's say you have a computer parts business.  Let's say it's called "lcdw" for "Linux computer discount warehouse."  :)  You now have a Swing application that your employees use for various purposes.

You have inventory management people, to maintain a certain minimum stock in the warehouse.  You have salespeople who man the phones, see the inventory and answer the phone for orders.  You have people who package the orders up and ship them.  There may be several applications which access the same database in different ways, some of which may be swing apps and some may be hardware monitoring of a sophisticated warehouse system.

Now you want to go all .com and make lcdw.com.  Now you have a web-based UI which accesses the same business logic that your swing app hits, to make sure that no matter where the request came from it gets handled the same way.

If you put business logic in your buttons and grids and panels, then that's all impossible and you're stuck rewriting a new app with the same functionality but using different display technology.

---

### Post by kevinharper on 2012-10-17
Thank you guys for the input and the links.

This is for a class. But I am going beyond the requirements by adding a GUI and wanting to open/save files with a window that lets the user navigate through their directories.

I am reading Test First website right now. Thank you for the warehouse example and all other suggestions. This has helped a lot! I'll post the finished product later tonight, as soon as I am done with it.

---

### Post by PatrickD-52761 on 2012-10-19
> **kevinharper said:**
> Thank you guys for the input and the links.

This is for a class. But I am going beyond the requirements by adding a GUI and wanting to open/save files with a window that lets the user navigate through their directories.

I am reading Test First website right now. Thank you for the warehouse example and all other suggestions. This has helped a lot! I'll post the finished product later tonight, as soon as I am done with it.

How are you creating the GUI? I'm asking because if you're using something like Netbeans or Eclipse, and using the JavaFX features (or Swing, or whatever Oracle is using), it will create the classes and methods for your GUI. You just need to create the classes and methods for the "magic behind the scenes" (actual functionality).

I would go through your list and group things together by whether they are part of the Presentation layer (the GUI and it's buttons or labels), or Utility Layer (the functionality behind the buttons).  If you're not using a GUI, then the Presentation Layer would be anything the user sees, and the Utility Layer is everything that happens behind the scenes.

In other words, if it interacts directly with the output (GUI or text based), then it goes in the Presentation layer (things like putting the result into a label, or assigning the text from a box to a variable, for example).  Otherwise, it goes into the Utility Layer.

Also, it will probably be easier to make suggestions after seeing your code. Even if it's not the GUI version of the code, we could probably tell you what should go where.

Have a great day:)
Patrick.

---

### Post by kevinharper on 2012-10-20
Thank you! Still working on it.

I should have a fully functional program later tonight. I will post code then.

---

### Post by KdotJ on 2012-10-20
If you're new to programming and really want to understand design etc, I would strongly recommend coding the GUI as opposed to using a GUI creator like the one Netbeans offers. I'm not saying they're bad, just tat you will not fully understand what's going on behind the scenes.

---

### Post by kevinharper on 2012-10-21
Using Eclipse.

I am having an issue with the following code:
```
private Record[][] parseFile(File f){
		Record lineItem[] = new Record[5];
		Record lineItemArray[][] = new Record[5001][5];
		String[] dataCell;

		int rowCount = 0;
		
    	try{
    		FileInputStream fstream = new FileInputStream(f);
    		DataInputStream in = new DataInputStream(fstream);
    		BufferedReader br = new BufferedReader(new InputStreamReader(in));
    		String strLine;
    		
    		while ((strLine = br.readLine()) != null && rowCount <= 5000){
    			System.out.println("strLine: " + strLine);
    			dataCell = strLine.split(",");
    			    //if column missing from row
    				if(dataCell.length != 5){
//    					lineItem[0] = new Record(0, "CORRUPT FILE", "CORRUPT FILE", 0, 0);
    					System.out.println("record[0]: " + lineItem[0]);
    					break;
    				}

    				//if a data cell is empty
    				for(int i=0; i < 5; i++){
    					if(dataCell[i] == ""){
//    						lineItem[0] = new Record(0, "CORRUPT FILE", "CORRUPT FILE", 0, 0);
    						break;
    					}
    				}

    			int ID = Integer.parseInt(dataCell[0]);
    			System.out.println("ID: " + ID);
    			String Description = dataCell[1];
    			System.out.println("Description: " + Description);
    			String Color = dataCell[2];
    			System.out.println("Color: " + Color);
    			int Quantity = Integer.parseInt(dataCell[3]);
    			System.out.println("Quantity: " + Quantity);
    			float Value = Float.parseFloat(dataCell[4]);
    			System.out.println("Value: " + Value);
    			lineItem[rowCount] = new Record(ID, Description, Color, Quantity, Value);
    			lineItemArray[rowCount][0] = lineItem[rowCount];
    			System.out.println("lineItemArray: " + lineItemArray[rowCount][0]);
    			rowCount++;
    		}
    		
    		in.close();
    		
    		//if file has too many records
    		if (lineItem.length > 5000){
//    			lineItem[0] = new Record(0, "FILE TOO BIG", "FILE TOO BIG", 0, 0);
    		}
    	}
    	catch (Exception e){
    		//System.err.println("Error: " + e.getMessage());
    	}
    	
		return lineItemArray;
    }
```

The error is somewhere around
```
int Quantity = Integer.parseInt(dataCell[3]);
```
because the values print up until Quantity.

---

### Post by KdotJ on 2012-10-21
What is the error you are getting?

Are you positive that the data in dataCell[3] is of type int?

---

### Post by kevinharper on 2012-10-21
No error - the array gets set to "null". See all of the println's? I added it on there to debug. The last thing printed to console is output from
```
System.out.println("Color: " + Color);
```

> Are you positive that the data in dataCell[3] is of type int?
It is not (or at least I don't think so). My understanding is that
```
FileInputStream fstream = new FileInputStream(f);
    		DataInputStream in = new DataInputStream(fstream);
    		BufferedReader br = new BufferedReader(new InputStreamReader(in));
    		String strLine;
    		
    		while ((strLine = br.readLine()) != null && rowCount <= 5000){
    			System.out.println("strLine: " + strLine);
    			dataCell = strLine.split(",");
```
results in dataCell containing String. The error occurs when trying to cast it as an int with
```
int Quantity = Integer.parseInt(dataCell[3]);
```
But there should be no problem b/c it works with
```
int ID = Integer.parseInt(dataCell[0]);
```

---

### Post by kevinharper on 2012-10-21
It is DEFINITELY in that place.
The following
```
dataCell = strLine.split(",");
for(String dc : dataCell)
    System.out.println("dataCell: " + dc);
```
Yields:
dataCell: 1
dataCell:  description test
dataCell:  yellow
dataCell:  10
dataCell:  3.40

Something is going on when casting string "10" into int 10.

---

### Post by trent.josephsen on 2012-10-21
I suspect KdotJ meant to say "Are you positive dataCell[3] is a String that contains an integer?" not just "is of type int" because calling Integer.parseInt on something that's already an int wouldn't make sense (despite the poor naming schema).

Edit: whoops, too slow for that suggestion. Still, maybe try printing dataCell[3] right before parsing it to make sure it hasn't changed? And put quotes around it in the output so you can see if it has leading or trailing whitespace. Integer.parseInt() will get confused by strings that contain anything other than decimal digits and an optional leading minus sign.

---

### Post by kevinharper on 2012-10-21
You guys, are a PC Gods among men.

It was a leading space! My CSV had ", 10"!

OMG! I racked my brains on this for days!

---

### Post by KdotJ on 2012-10-21
> **trent.josephsen said:**
> I suspect KdotJ meant to say "Are you positive dataCell[3] is a String that contains an integer?"

lol yes I did indeed! Thanks

Kevin, 
 you could use the [trim]("http://docs.oracle.com/javase/1.4.2/docs/api/java/lang/String.html#trim()") method for Strings to remove leading and trailing whitespace. Something like:

```
int Quantity = Integer.parseInt(dataCell[3].trim());
```

---

### Post by spjackson on 2012-10-21
> **kevinharper said:**
> 
It was a leading space! My CSV had ", 10"!

OMG! I racked my brains on this for days!

If you didn't have a catch block that does nothing with the exception, you may well have found it earlier, with a message like:
```

Exception in thread "main" java.lang.NumberFormatException: For input string: " 123"
	at java.lang.NumberFormatException.forInputString(NumberFormatException.java:65)
	at java.lang.Integer.parseInt(Integer.java:481)
	at java.lang.Integer.parseInt(Integer.java:527)


```

---

### Post by kevinharper on 2012-10-22
Thanks guys. I added the ".trim()" attribute (is it an attribute?) to the casts. And I also un-commented the catch block statement.

---

### Post by trent.josephsen on 2012-10-22
trim() is in fact a method, not an attribute.

It would be better, rather than just catching every exception in the same place, to wrap only the stuff that throws the exception you want to catch, and name it explicitly in the catch. That way, exceptions you weren't thinking about, like NumberFormatException, get thrown all the way up and dump to the screen to let you know what went wrong and where. When a try-block contains many lines of code that can throw probably dozens of different exceptions, you don't want to catch them all with the same handler.

---

