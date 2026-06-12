---
title: "what does it mean to download ruby or...?"
date: 2008-07-26
forum: New to Ubuntu
---

### Post by adamogardner on 2008-07-26
So when I got my computer I did so to write a program for a robot.  I downloaded a python IdE.  (now just because I bought a machine to write a program for a robot doesn't mean I have a clue as to what I'm doing) But as I go and download certain packages I am required to download additional python (ruby too on occasion) packages.  What are these packages?  Why aren't they included in the IDE library?  how do they effect my computer?  Is my computer better off or more versatile because I have some ruby packages installed?

---

### Post by Pro-reason on 2008-07-26
If I given program requires another program, then it requires it.  That's why APT (via Synaptic or whatever) installs the extra program.  I'm not sure what you are really asking.

Perhaps you are used to operating systems whose applications tend to install multiple redundant versions of the libraries that they need, and bloat their installers with such hidden dependencies.

---

### Post by adamogardner on 2008-07-26
or perhaps this is my first computer and I'm not used to anything at all.
the redundency I'm asking about is why I am seemingly installing python packages over and over again.  And whay aren't they all included in the ide library, and what are the general differences between all these computer-language-packages?   sorry I didn't make sense.  I am still learning the language.

---

### Post by SOULRiDER on 2008-07-26
How did you install the Python IDE? Did you use th eincluded package manager?

---

### Post by adamogardner on 2008-07-26
honestly I don't remember   probably apt-get install  maybe since thats what I prefer to use.  it's in my menu and reads python v2.5   with a yellow and blue icon

---

### Post by era86 on 2008-07-26
Are you referring to the different versions of the Python libraries?

---

### Post by SOULRiDER on 2008-07-26
What you probably did was
```
sudo aptitude install python
```
(although it should come installed)
If you want to install ruby just do the same thing.
```
sudo aptitude install ruby
```
That will install ruby and all applications that need Ruby will be able to use it.

---

### Post by Pro-reason on 2008-07-26
> **adamogardner said:**
> 
the redundency I'm asking about is why I am seemingly installing python packages over and over again.

Over and over again?  What are you referring to exactly?

I assumed you were talking about the dependencies that were pulled in when APT installed the program.  But are you talking about something else?  Is there some message about installation that comes up when you try to utilise the program?

I'm having a hard time understanding exactly what is happening.  Perhaps a screenshot would clarify things.

---

### Post by adamogardner on 2008-07-26
i wish I knew exactly what packages they were and when.  I kept no history, but perhaps ubuntu did.  Essentisally yes these packages arise when I install another package so they are "dependencies."  All I am trying to understand is what are the for?  why isn't python just one program, but something I have to get in bits and pieces.  These Pythion packages are to help the computer translate the progrgams writing; Is this correct?  I'm just trying to get a view of the architecture behind what is going on.  I can't even explain it that well.  So probably nothing you say on  the subject would be too condescending.

---

### Post by cariboo on 2008-07-26
IF you open up Synaptic and go to File-->History it will give you a list of packages you have installed. You can then search Synaptic for a particular package and see what that package does in the package description. The reason they are not all installed with the IDE, is that the IDE just has basic libraries to get you started, for more functionality in you prgrams you need more libraries. most of the libraries are only a couple of kilobytes in size so you don't have to worry about filling you hard drive with them.

JIm

---

### Post by Pro-reason on 2008-07-27
> **adamogardner said:**
> I'm just trying to get a view of the architecture behind what is going on.  I can't even explain it that well.  So probably nothing you say on  the subject would be too condescending.

Things are made of other things, and rely on other things.  For example, all the appliances in your home use electricity from the sockets in your walls; you only have one type of shampoo (if you're the average dude); the bowls in your kitchen work fine or cereal, soup or ice-cream.

Now, you could do things differently.  You could install a separate electricity supply for your lighting and your other appliances.  You could have one shampoo that you use in the shower, and one that you use in the bathtub.  You could buy separate bowls for different foodstuffs.  Most of the time, all of that would be pointless.  You would be doubling up on stuff, and wasting money and resources.

Similarly, if I write a program that runs a test on a file, and then compresses it as either gzip or bzip2 depending on which will yield a better compression, then there are two ways I could implement this.  

Firstly, I could take the separate-shampoos approach, and include software that handles the compression in my own software.  This will probably double the size of my program.  Even though my program actually contains several other bits of software, I package it as one, and users download it as one.  They are fooled into thinking that there is one big monolithic program that just does what it does.

The other way to do it is the one-shampoo approach.  I might decide that it is wasteful to include the gzip and bzip2 programs inside my own, when the end user probably already has those programs installed on their computer.  So, what I do is make my program simply use what is already installed.  If the necessary software happens not to be installed, the software package manager will tell the user that they need to install it in order to use my program.

So, if the user has it already, then I save them from downloading and installing a redundant copy.  If they user doesn't have it already, then they just download it.  In this latter case, the result is effectively the same as with the other approach, but it's more transparent (the user can see that my software is made up of component parts, rather than me trying to hide that fact).

Windows programs normally work in the separate-shampoos way, which is wasteful, but helpfully hides the workings of the software from people who might be fazed by it.  Linux programs normally work in the one-shampoo way, which is much more efficient, but will confuse you if you are used to the other way.

I'm not familiar with the Python packages, but I'm sure that any other software pulled in as dependencies is pulled in because it needs to be.

---

