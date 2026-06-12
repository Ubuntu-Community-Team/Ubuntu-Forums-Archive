---
title: "Using Visual Basic in Excel"
date: 2012-02-11
forum: Programming Talk
---

### Post by bradley002 on 2012-02-11
In my job I have a large amount of data in an Excel sheet (go figure, right :)). I have been using filters and formulas to sort it, but it would be much more powerful to use programming functions and algorithms to analyze the numbers. I just recently realized that you can use visual basic functions directly within Excel.

I have no experience with Visual Basic or doing much of anything practical with programming outside of university. I want to automate processes like this:

- Search column A for a number, N between X and Y

- If column A contains N, move to next column over (B) and search for number N2 between X2 and Y2

- If column B contains N2, take standard deviation of columns R to Z. 

Well, I suppose there are many different types of algorithms I'd like to use and it would be tedious to describe them all, but what do I need to study to use basic programming functions on the numbers like If, Then, Else, For, While?

---

### Post by Lars Noodén on 2012-02-11
If you upgrade to LibreOffice then you can do your scripting in Python or Javascript.

---

### Post by bradley002 on 2012-02-11
They would not let me upgrade. They sort of treat us like babies here. We can get permission to add a few select programs, but something like a new Office package would be lost in the abyss of security requests.

Are the kinds of functions I am describing not inherent in the capabilities of Excel 2007?

---

### Post by Lars Noodén on 2012-02-11
You can run Portable LibreOffice from a UBS stick:

[http://portableapps.com/apps/office/libreoffice_portable](http://portableapps.com/apps/office/libreoffice_portable)

That will get you up and running without installing software.  Then you can script in Python or Javascript.

But for questions on legacy applications we're going to have to refer you to some other forum.

---

### Post by muteXe on 2012-02-11
To be honest, I would use MS Access. Easy to get the data in there and easy to knock up some queries to get want you want.

---

### Post by eriktheblu on 2012-02-11
Spreadsheets are good for (personal opinion only):
1. Small but complex calculations where only one figure is needed. 
2. Large but simple calculations that are not repeated with any regularity.

Anything that involves complex calculations, data relationships, or repetitive calculations is more appropriately applied with a database. In most cases, Excel is for people who don't know or don't have Access.

Not entirely understanding what you're calculating, but it would seem Access (if available, it is pricey software) would suit you better.

Failing that, you can probably use the 'lookup' function in Excel without bothering with VB (used to do a lot of that before I learned Acess).

---

### Post by trent.josephsen on 2012-02-11
I'm surprised to see recommendations for Access, we should be pushing a real database like MySQL or SQLite. </hahaonlyserious>

OP:  If you really want help with Excel formulas, you'd be well advised to ask in a forum where people would be likely to know about that kind of thing.  Otherwise, as you have already discovered, you're likely to get a bunch of people telling you you're using the wrong tool and explaining why you should switch to their favorite program instead.

---

### Post by bradley002 on 2012-02-11
Well, I figured Visual Basic is a programming language right? Maybe its versatility within Excel is limited. Oh well, thanks.

---

### Post by ofnuts on 2012-02-11
> **eriktheblu said:**
> Spreadsheets are good for (personal opinion only):
1. Small but complex calculations where only one figure is needed. 
2. Large but simple calculations that are not repeated with any regularity.

Anything that involves complex calculations, data relationships, or repetitive calculations is more appropriately applied with a database. In most cases, Excel is for people who don't know or don't have Access.
A Database won't do really complex computations. But you can mix the two, a spreadsheet can be updated from a database (I have an Excel spreadsheet that auto-updates its data from an Oracle DB).

The one thing spreadsheets are very good at is user-tailored data display.

---

### Post by eriktheblu on 2012-02-12
> **trent.josephsen said:**
> I'm surprised to see recommendations for Access, we should be pushing a real database like MySQL or SQLite.
Sometimes you just have to go with what you know. Databases other than Access are not an option for me at work, and I have no use for databases outside of work.

> **ofnuts said:**
> A Database won't do really complex computations. Perhaps different definitions of complex. My main point I guess is that spreadsheets are better for quick setup, where databases are better for repetitive calculations. Again, still just opinion here.

> **bradley002 said:**
> Well, I figured Visual Basic is a programming language right? That's debatable, but OK. > Maybe its versatility within Excel is limited. Oh well, thanks.
There's an old joke comparing the US space program with the USSR. When they discovered that their ball point pens didn't work in zero gravity, the US spent millions of dollars developing a pen that fed ink using a pressurized cartridge. The Soviets switched to pencils.

From what you're describing (without fully understanding your formula) I think it is likely that you can accomplish this without resorting to VB. Much simpler to use the built in logical and mathematical functions of Excel.

Perhaps something like:
```
=if(A1<5 and A1>1 and B1>152 and B1<300,STDEV(R1:Z1),"Out of Range")
```

Again, not really understanding your specific goal so this may not be applicable.

---

### Post by trent.josephsen on 2012-02-13
> **eriktheblu said:**
> Sometimes you just have to go with what you know. Databases other than Access are not an option for me at work, and I have no use for databases outside of work.

I was kidding.  Mostly.  Although I do think lumping the likes of Access into the same group as MySQL, Informix, Oracle, etc., and even SQLite, is an abuse of the terminology.  But that's a topic for another day.

---

