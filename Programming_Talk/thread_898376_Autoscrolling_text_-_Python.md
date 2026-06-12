---
title: "Autoscrolling text - Python"
date: 2008-08-23
forum: Programming Talk
---

### Post by aktiwers on 2008-08-23
I want to write a small program that displays auto-scrolling text (with Tkinter?),or at least some GUI.

The text should come from a text .txt file.

I am still a beginner in Python and can't really grasp how to do this? Like how to control the timings from each line to show up etc?

Would a loop calling each line be the right way to do this? 

Or how would you approach this? All help/links will be very appreciated :)

---

### Post by aktiwers on 2008-08-23
Okay I settled with using the readlines() and the Timer() class.

Gonna post some code if I get it to work :)

---

### Post by aktiwers on 2008-08-23
Okay I can't get this to work :(

I want it to print a new line from the text file every 4 second..   but instead it waits 4 seconds
and then print the whole text file..  can anyone help me out with this?
(Sorry about the danish code, let me know if it is I need to translate it)
[php]
from threading import Timer
# Insaet sti paa text dokument imellem "". (boer ikke aendres)
dokument = "test.txt" 

# Indstil hastigheden paa texten her
#(4.00 = 4 sekunder) 
tid = 4.00

"""
Beskrivelse af funktionen
"""
def skriv():
    
    f = open(dokument, "r") # indlaeser text dokument
    linie = f.readlines() 

    count = len(linie) # taeller antal linier i dokument
    print count
    
    
     # Loop der fungere som scrolling text
    def hejsa():
        for x in range(0, count):    
            
            print linie[x]
            t.cancel()
          

    # En timer
    
    t = Timer(tid, hejsa)
    t.start()
    
  
[/php]

---

### Post by aktiwers on 2008-08-23
Argh!! Nevermind! Got it !

[php]
def skriv():
    
    f = open(dokument, "r") # indlaeser text dokument
    linie = f.readlines() 

    count = len(linie) # taeller antal linier i dokument
    print count
    
    
     # Loop der fungere som scrolling text
    for x in range(0, count):    
        time.sleep(3)
        print linie[x]
[/php]

---

### Post by cmay on 2008-08-23
> Argh!! Nevermind! Got it !
 great :)

btw
it might  be an advantage not to use danish in code.
not that i have trouble reading it since i am from denmark my selve.
but if anyone else reads it and dont know danish it can prevent some  from answering.
good luck whit your project :)

---

### Post by aktiwers on 2008-08-23
Hey Thanks or Tak :)

Now my next problem is to get it into tkinter :(

---

### Post by days_of_ruin on 2008-08-23
Don't use Tkinter, its ugly.

I would recommend [pygtk]("http://pygtk.org/").It has
functions to scroll text btw.

And use glade to design the ui.Great tutorial [here]("http://www.micahcarrick.com/12-24-2007/gtk-glade-tutorial-part-1.html")

---

