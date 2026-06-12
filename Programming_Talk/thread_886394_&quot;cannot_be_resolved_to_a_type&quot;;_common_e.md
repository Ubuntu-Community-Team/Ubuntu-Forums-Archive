---
title: "&quot;cannot be resolved to a type&quot;; common error, but for much more complex code."
date: 2008-08-11
forum: Programming Talk
---

### Post by gimfred on 2008-08-11
I've got a single .java file, which has been working fine until I tried to move things to their own methods.

I was getting the old:
```

Cannot make a static reference to the non-static method menuSoccerJerseyBar() from the type SoccerJersey_000_000_001

```

so I edited my code to the following:
```

	menuSoccerJerseyBar frameMenuSoccerJerseyBar = new menuSoccerJerseyBar();
	scrollPaneCartSelection frameScrollPaneCartSelection = new scrollPaneCartSelection();
	clubSelector frameClubSelector = new clubSelector();
	shirtQuantity frameShirtQuantity = new shirtQuantity();
	soccerTeamHomeAway frameSoccerTeamHomeAway = new soccerTeamHomeAway();
	shirtSize frameShirtSize = new shirtSize();
	cartButtons frameCartButtons = new cartButtons();
	

```

> ----------
1. ERROR in SoccerJersey_000_000_001.java (at line 550)
        menuSoccerJerseyBar frameMenuSoccerJerseyBar = new menuSoccerJerseyBar();
        ^^^^^^^^^^^^^^^^^^^
menuSoccerJerseyBar cannot be resolved to a type
----------
2. ERROR in SoccerJersey_000_000_001.java (at line 550)
        menuSoccerJerseyBar frameMenuSoccerJerseyBar = new menuSoccerJerseyBar();
                                                           ^^^^^^^^^^^^^^^^^^^
menuSoccerJerseyBar cannot be resolved to a type
----------(there are 14 of these, only the method name changes.

It is an assignment, so I appreciate that people may not feel they can answer, however I've been at this for well over 8 hours studying my text book, lecturers notes Sun's api and other Google searches.

So I get that it isn't finding the methods such as menuSoccerJerseyBar, but they are all public and in the same file. It is a single class! And they were working until I added 

I'm asking how do I tell the compiler to find the public methods in the class? I've tried what I though was the fully qualified name:
SoccerJersey_000_000_001.menuSoccerJerseyBar
etc...
but that just adds 
SoccerJersey_000_000_001 to the end of type.


++++++++++++++++++++++++
p.s. this is crazy; I had to change the source code to a .doc file to upload because it was too big to fit in the other file types!

---

### Post by Zugzwang on 2008-08-11
[LIST=1]
[*]No one will open .doc files here. If your file is too big, put it into a .zip file or so. However, nobody will read such long texts anyway, so make *minimal examples* showing your problem in order to get useful answers.
[*]The following line:
 ```

menuSoccerJerseyBar frameMenuSoccerJerseyBar = new menuSoccerJerseyBar();
 
```
means that you declare an Object of *class* menuSoccerJerseyBar named frameMenuSoccerJerseyBar and initialise it with a new instace of the class menuSoccerJerseyBar. If "menuSoccerJerseyBar" is no class but a method as you wrote, you cannot instantiate it since you cannot instantiate methods in Java. If you are trying to so this, then you are mixing methods and classes in your terminology.
[*] We will not help in solving the assignment, just give you some hints on where the problem could be.
[/LIST]

---

### Post by Reiger on 2008-08-11
Before you went to change all your code you should've read the error:

It says: this method you wanna use affects an object. You don't have an object it affects, as you call it statically. 
```

[COLOR="Navy"]TypeExpr[/COLOR].[COLOR="Green"]Method[/COLOR] c.f.: [COLOR="Navy"]JOptionPane[/COLOR].[COLOR="#008000"]showMessageDialog[/COLOR]("my message");

```

Hence the solution is to create an object first: 
```

[COLOR="#000080"]TypeExpr[/COLOR] o = new [COLOR="Green"]TypeExprObjectConstructor[/COLOR](args);
c.f.:
[COLOR="Navy"]JFrame[/COLOR] frm = new [COLOR="#008000"]JFrame()[/COLOR]; /* or new JFrame("there may exist multiple constructors for certain object types!") */

```

Then call the method. Assuming your object is 'simply' a collection of fields (object vars) and methods; in your case it likely would be:
```

TypeExpr tpe = new TypeExpr()
tpe.methodName();

```

Just fill in the blanks... ;)

---

### Post by gimfred on 2008-08-12
@Zugzwang: Yeh, I don't know why I didn't think of zip file... I musta been totally hazed. 

And I specifically said it was an assignment so people would only hint. I was using the forum as a vent of my frustration at myself for not getting it as well as hope that someone would say something that makes the penny drop. Thanks for both replies. 

I'm still not understanding why (other than I'm mixing terminologies up... ) I can't call my methods from the same class. I thought that was the idea of making them public? 

@Zugzwang: It isn't <method call> <variable> = new <method(parameters)> to create a new instance of the method? Hmmm looking at my own sentence, that doesn't make sense. Oh well, it was going too fast for me anyway.

I read that in Java, static isn't English static but programing historical static... just haven't figured out what that means.

I think I'd understand the error if it was calling methods from a different class, but they are all in the same class. Argh! now I need a drink!

---

### Post by Zugzwang on 2008-08-12
> **gimfred said:**
> I'm still not understanding why (other than I'm mixing terminologies up... ) I can't call my methods from the same class. I thought that was the idea of making them public? 

You *can* call methods from the same class and in they don't even need to be public in this case. You just don't instantiate them before calling.

> **gimfred said:**
> 
@Zugzwang: It isn't <method call> <variable> = new <method(parameters)> to create a new instance of the method? 

No, you cannot instantiate methods in Java. This is not functional programming. You should seriously brush up your understanding. Since the .doc file you posted contained German control commands, let me give you a link to a (web-)book in the same language that might be of help: [http://www.galileocomputing.de/openbook/javainsel7/]("http://www.galileocomputing.de/openbook/javainsel7/"). Have a look at chapter 3 which deals with classes, objects & methods.

---

### Post by Reiger on 2008-08-12
Yes in that case it's typically:
```

[COLOR="Purple"]**this**[/COLOR].[COLOR="DarkSlateBlue"]doSomeStuff[/COLOR]([COLOR="Green"]someArgs[/COLOR]);

```

---

### Post by gimfred on 2008-08-13
> Since the .doc file you posted contained German control commands
It did? Don't worry, I can find the book in English via Google, but I have no idea how the German control commands got in there... it comes from my source... :)

Y'don't mean this? > Argh! now I need a drink! Schnell! (or is it Himmel!)

---

