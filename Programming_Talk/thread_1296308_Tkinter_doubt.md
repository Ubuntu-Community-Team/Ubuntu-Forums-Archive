---
title: "Tkinter doubt"
date: 2009-10-20
forum: Programming Talk
---

### Post by 7raTEYdCql on 2009-10-20
I have a few problems that i am facing with Tkinter, and need help.

1- My code looks somewhat like this:
```

def draw(args):
	#code
	
	root.mainloop() #This is where i want my Tkinter window to update, without requiring it to be closed
	time.sleep(1)
	
def main():
	from Tkinter import *

	root=Tk()
	while(1):
		#code
		draw(args)

```
Instead of mainloop, i have identified a method called update, but don't know how it works. Can someone help.

2- How can you draw a simple table with information on a tkinter canvas.

---

### Post by lavinog on 2009-10-20
Can you post the actual code?
the code you posted doesn't run.

main() isn't called
args is not defined
root is not passed to draw

edit: is this more like what you want?
```

def draw(root):
        import time
	#code
	
        root.mainloop() #This is where i want my Tkinter window to update, without requiring it to be closed
        time.sleep(1)
	
def main():
	from Tkinter import *

	root=Tk()
	while(1):
		#code
		draw(root)
main()

```

---

### Post by 7raTEYdCql on 2009-10-20
I am sorry for misguided information(which i assumed) in the code.

My whole point is, how do we update the Tkinter window, everytime i enter the while loop? In my code that runs, the window updates itself, everytime i close it. Which isn't what i want. I want a self-updating window, every 1 second or something. Can someone please help. My code formation is still somewhat mentioned above.

---

### Post by lavinog on 2009-10-20
I think it would be easier if you had something I could work with.

I am not understanding why you need the form updated every second.

---

### Post by 7raTEYdCql on 2009-10-21
It is something like this, Main calls draw. Which does something to the tkinter window, depending on its received arguments. Then time.sleep(1), makes the Tkinter window wait for some time, without undergoing any change. On returning to main, draw is called with a new set of arguments, which should again make changes to the Tkinter screen.

I want to know, how to update the Tkinter window??(Which should ideally update depending on the sleep time mentioned.)

---

### Post by stevescripts on 2009-10-21
> **i.mehrzad said:**
> I have a few problems that i am facing with Tkinter, and need help.

...

2- How can you draw a simple table with information on a tkinter canvas.

hmm ... if you want a table - why not look at a table widget, rather than drawing it on a canvas?

TkTable - [http://tkinter.unpythonic.net/wiki/TkTable](http://tkinter.unpythonic.net/wiki/TkTable)

Steve
(PS - with Tk, you should avoid update whenever possible, FWIW)

---

### Post by 7raTEYdCql on 2009-10-22
The purpose of, root.mainloop() is to display the top level widget, root, along with all the widgets packaged in it. 

Is root.update(), a replacement for root.mainloop(), except that 'root' will update itself, everytime this statement is executed.
Is this thinking correct??

One more problem i am facing, is where should, root.mainloop() be located in the program. Is it allright if it is encountered once, i.e. at the end of the entire program. 

Can someone please help, i have an assignment which has to be submitted on the coming weekend, and can't seem to figure this out.

---

