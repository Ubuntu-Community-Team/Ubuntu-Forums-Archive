---
title: "Is this efficiant?"
date: 2009-08-07
forum: Programming Talk
---

### Post by swoll1980 on 2009-08-07
[Python] Or was there a better way to do this?

---

### Post by Can+~ on 2009-08-07
Do you have something against the [PHP] tags? They need some love too, you know.

---

### Post by doas777 on 2009-08-07
prolly. it doesn;t look inefficient. your only loops are defined by user input, so theres nothing you can do to reduce the number of calls. its O(n).

---

### Post by swoll1980 on 2009-08-07
> **Can+~ said:**
> Do you have something against the [PHP] tags? They need some love too, you know.

Would you think I was stupid if I had no idea what you were talking about?

---

### Post by doas777 on 2009-08-07
> **swoll1980 said:**
> Would you think I was stupid if I had no idea what you were talking about?

the sites "Code" tags. when you wanna post code, just click the bold "#" at the top of the post editor pane, and put your code within the tags. 
```

that way it
   looks
   like
   this

```

---

### Post by Can+~ on 2009-08-07
> **swoll1980 said:**
> Would you think I was stupid if I had no idea what you were talking about?

Yes, but then again, I think everyone is stupid. That's because my mom told me I was special... oh wait...

Anyway, back on topic, I meant using the PHP tags instead of uploading a PDF. Which has the added bonus of adding syntax highlighting. 

[PHP]#backup calculator 1.1
#Nolan Bloor
#03 Aug 2009
def main():
    print "Welcome to the T & N backup calculator"
    maxSpace = input ("What is the capicity of the drive? (MBs) ")
    usedSpace = input ("How much space ( MBs) are you currently useing?    ")
    avSpace = maxSpace - usedSpace
    print
    print "You currently have",avSpace,"MBs available to you"
    print
    userChoice = "1"
    while userChoice == "1" or userChoice == "2":
        userChoice = showMenu()
        if userChoice == "2":
             newSpace = subtract(avSpace,maxSpace)
             if newSpace == "fault":
                 print "Sorry try again."
                 print
             else:
                 print
                 print "Your new available hard drive space would be", newSpace,"MB"
                 print
        elif userChoice == "1":
             newSpace = add(avSpace)
             if newSpace == "fault":
                 print "Sorry try again."
                 print
             else:
                 print
                 print "Your new available hard drive space would be", newSpace,"MB"
                 print
        else:
             print "Good Bye"
def add(avSpace):
    addedSpace = input ("How much space does the backup require?    ")
    pWeek = input ("How many times a week would you like to make this backup?    ")
    perWeek = pWeek * addedSpace
    newSpace = avSpace - perWeek
    print
    print "This backup requires",perWeek,"MBs of drive space"
    if newSpace < 0:
        print
        print "You do not have enough space for this backup."
        print
        newSpace = "fault"
    return (newSpace)
def subtract(avSpace,maxSpace):
    subSpace = input ("How much space did the backup use?    ")
    newSpace = avSpace + subSpace
    if newSpace > maxSpace:
        print
        print "That's more space than you started with. You must be smokin'
something!"
        print
        newSpace = "fault"
    return (newSpace)

def showMenu():
    userChoice = "0"
    while userChoice == "0":
        print "Enter 1 to add backup."
        print "Enter 2 to remove a backup."
        print "Enter 3 to exit."
        userChoice = raw_input ("Enter your choice   ")
        if userChoice != "1" and userChoice != "2" and userChoice != "3":
            print
            print "Please choose a number between 1-3"
            print
            userChoice = "0"
    return (userChoice)
main()
[/PHP]

*edit: I'm pretty sure there other ways to get the Free space available on the hard disk. There's [an interesting thread about this]("http://mail.python.org/pipermail/python-list/2001-January/065911.html") (read the subsequent responses)

*edit2: Whoops, wrong link above, fixed.

*edit3: Well, now that I've read the whole code: You should probably code the "functionality" of an application before delving into the user interface. It's better having something useful without an interface than an interface without something useful behind. 

This is specially to make a distinction between "working code" (Back-end) and "user input" (Front-end), you may later want to replace the Command line interface with a GTK+ GUI or something.

---

### Post by swoll1980 on 2009-08-07
The program above is not intended to ever be used. I'm just trying to learn the basics of Python as of right now. This was a exercise in the lab section of my text book. Since I'm not being graded on this particular exorcise, there's no way for me to know if I did it efficiently. That's where you guys come in. I did the php code by hand one time, and I was like "Wow that's a pain in the butt" I found the php code button on the forums here now that I knew what I was looking for. The program is supposed to calculate how much disk space they would have after the addition, or removal of a back up. It is to have a menu, and it is to have error messages if the user doesn't follow the instructions, or makes a mistake.

---

### Post by doas777 on 2009-08-07
> **swoll1980 said:**
> The program above is not intended to ever be used. I'm just trying to learn the basics of Python as of right now. This was a exercise in the lab section of my text book. Since I'm not being graded on this particular exorcise, there's no way for me to know if I did it efficiently. That's where you guys come in. I did the php code by hand one time, and I was like "Wow that's a pain in the butt" I found the php code button on the forums here now that I knew what I was looking for. The program is supposed to calculate how much disk space they would have after the addition, or removal of a back up. It is to have a menu, and it is to have error messages if the user doesn't follow the instructions, or makes a mistake.

"algorithmic efficiency" is usually applied to looping data structures, and is measured in what is called "Big O" notation. you usually hear it applied to sort or search code, or list processing tasks.

as far as your code is concerned, try to loop as little as possible and make sure your exit conditions (the circumstances under which loop ends) are solid, and occur as soon as possible. 

other than that, try to accomplish what you want in the fewest operations. that does not necessarily mean fewer lines (a string of 6 method calls chained together is equally efficient to 6 lines with one call each). 

when your working with langagues like python, java, and C#, the inefficiency of the interpreter is probably a bigger hit to performance than most of the code you could write.

---

