---
title: "Trivia game tkinter GUI need help"
date: 2010-09-28
forum: Programming Talk
---

### Post by trikster_x on 2010-09-28
I am trying to write a simple trivia program.  I have it working fully as a terminal program, but I would like to get it running with a GUI.  I have gotten it 90% working as far as I can tell, but I can't seem to get everything to refresh itself after you answer a question. Please keep in mind this is actually my first program I have used the GUI toolkit that involves more than simply displaying a random message, so if you can keep the explanations as simple as possible, it would be great. 

```
#!/usr/bin/python
import random
from Tkinter import*

q1 = ['test question1' , 'test ans1' , 'test ans2', 'test ans3' , 'test ans4' , '1' , 'hint' , 'number' , 1]
q2 = ['test question2' , 'test ans1' , 'test ans2', 'test ans3' , 'test ans4' , '2' , 'hint' , 'number' , 2]
q3 = ['test question3' , 'test ans1' , 'test ans2', 'test ans3' , 'test ans4' , '3' , 'hint' , 'number' , 3]
q4 = ['test question4' , 'test ans1' , 'test ans2', 'test ans3' , 'test ans4' , '4' , 'hint' , 'number' , 4]
q = [q1, q2, q3, q4]
    
        
right = 0
asked = 0

root = Tk()
root.title('My Game')
root.geometry('400x300+100+70')

while right < 6:
    
    
    x = (len(q) - 1)
    z = random.randint(0, x)
    n = q.pop(z)
    
    quest = StringVar()
    quest.set((n[0],n[1],n[2],n[3],n[4]))

    hint = StringVar()
    hint.set((n[6],n[7],n[8]))  
       
    questlabel = Label(root, textvariable=quest, justify=LEFT)
    questlabel.pack(side=TOP)
    
    v = StringVar()
    input = Entry(root, textvariable=v, takefocus=1)
    input.pack()
    input.focus_set()
    
    def ans():
        if v == n[5]:
            mbox = Toplevel(root)
            label = Label(mbox, text='Correct!')
            label.pack()
            b = Button(mbox, text='Okay', command=mbox.destroy)
            b.pack()
            b.bind('<Return>')
        if v != n[5]:
            mbox = Toplevel(root)
            label = Label(mbox, text='Correct!')
            label.pack()
            b = Button(mbox, text='Okay', command=mbox.destroy)
            b.pack()
            b.bind('<Return>')
            
    mbutton = Button(root, text='Okay', command=ans)
    mbutton.pack(side=BOTTOM)
    
    root.mainloop()
        
    if right == 5:
        break

```

This is what I have so far.  The window opens and everything populates, but when I close the text box in the def, the root window doesn't reset with a new question and answer set.  I am going to eventually add a counter to keep score, and there will be a couple more loops for differing levels of difficulty.  It seems like this would be easy enough to implement if I can get past my current problem.  Any help on this problem is appreciated.

---

### Post by gmargo on 2010-09-28
root.mainloop() does not return (until the window is closed?), so you only get through the first pass of the while loop.  If you want to change the question, then you have to do it in response to a button event.

---

### Post by trikster_x on 2010-09-28
Thanks for the tip, it's much appreciated.  

So the easiest way to do it would be to have the button in my top level message box be tied to a command to destroy all the widgets in my root window and repopulate them?  Would that method allow me to include a counter to keep track of the number of questions that have been asked and the number of correct answers?  

I'll give it a go and see if I can get anywhere with the info you gave me.  Thanks again.

EDIT:  I did some testing and managed to get a second question to come up, but after a bit of digging, it seems the approach I am using absolutely will not work for what I need to do.  Looks like I get to do some reading on classes to get this thing doing what I want.  If anyone has any good reference sites on how to handle classes in tkinter, that would be great.

---

