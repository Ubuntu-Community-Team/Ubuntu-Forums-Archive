---
title: "Python/Tkinter noob stuck!"
date: 2010-11-22
forum: Programming Talk
---

### Post by CaptainMark on 2010-11-22
Can someone please point out what it is that Im obviously missing, im self teaching to write programs in python and just started on gui's using tkinter, ive attached my code, it doesnt do a lot but its a practice, can anyone tell me why my window title comes up as 'tk' instead of 'Secret' ```
#!/usr/bin/python3
# password
# a gui that reveals a secret when the password is entered
# mark skinner 20/11/2010

from tkinter import *

class Application(Frame):
    '''open a frame and start the widgets'''
    def __init__(self,master):
        super(Application, self).__init__(master)
        self.grid()
        self.create_widgets()

    def create_widgets(self):
        '''button, text, and entry widgets'''
        # intruction label
        self.inst_lbl=Label(self,text='Enter password to get the secret.')
        self.inst_lbl.grid(row=0,column=0,columnspan=2,sticky=W)
        # password label
        self.pwd_lbl=Label(self,text='Password: ')
        self.pwd_lbl.grid(row=1,column=0,sticky=W)
        # entry widget to accept password
        self.pw_entry=Entry(self)
        self.pw_entry.grid(row=1,column=1,sticky=W)
        # button for pw entry
        self.submit_bttn=Button(self,text='Submit',command=self.reveal)
        self.submit_bttn.grid(row=2,column=0,sticky=W)
        # text widget
        self.secret_txt=Text(self,width=35,height=5,wrap=WORD)
        self.secret_txt.grid(row=3,column=0,columnspan=2,sticky=W)
        # reveal command
    def reveal(self):
        contents=self.pw_entry.get()
        if contents.lower()=='secret':
            message='The secret is, you smell!'
        else:
            message='Wrong password, Im not telling you the secret.'
        self.secret_txt.delete(0.0,END)
        self.secret_txt.insert(0.0,message)

# main
root=Tk()
root.title=('Secret')
root.geometry=('300x150')
app=Application(root)
root.mainloop()


```Im obviously missing something stupid but Its driving me mad, ive written the #main section the same as another couple of gui practices and they have dont do this.

---

### Post by TheWeakSleep on 2010-11-22
if you change the line:
```
root.title=('Secret')
```
to read:
```
root.title('Secret')
```
It should work

---

### Post by CaptainMark on 2010-11-23
Doh!, Thanks

---

