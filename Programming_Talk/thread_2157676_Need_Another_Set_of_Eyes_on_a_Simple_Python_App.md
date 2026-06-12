---
title: "Need Another Set of Eyes on a Simple Python App"
date: 2013-06-26
forum: Programming Talk
---

### Post by sixstorm on 2013-06-26
Hello everyone. I am a CIT instructor at a technical college and have come up with a small C++ app to clock students in and out (some have coop jobs and it's hard to keep track of 20-40 students). The app I created (C++ version) earlier this year has worked out quite well, but some other instructors wanted to implement this in their class. I decided to rewrite the app in Python and use the Tkinter GUI to make it a lot easier than the previous version: all text/CLI based.
Most of the app is ready to go and the basic functionality is there. There are just a few things I need another set of eyes on, thus why I'm posting here.

Disclaimer: This is my first Python app (more than the basic stuff) so don't judge me. I've basically pieced tutorials together since that's how I learn programming the best.

This app is extremely simple: there are two listboxes(available students and present students) with Clock In, Clock Out and Exit buttons. Students come in, find their name in the AStudents listbox, select it and click on the Clock in Button. Done. If they have to leave early, they can find their name in the PStudents listbox, select it and click on the Clock out Button. All of these actions get written out into a log file (log file is named after the MM/DD/YYYY format), then another Python script emails it to the instructor.
I do have future plans on adding more things such as passwords for each student, an admin console, etc. But other instructors need this going by the end of the week, bugs or not.  

1) I have built in a "resume" feature to where if a student accidentally exits/closes the program, the instructor can just click on a resume menu item and all is well. When I try this out on the app, it will look at 'resume.txt', input the first name in the text file into the PStudent listbox, but give the error "TclError: bad listbox index "Cecil Huffines": must be active, anchor, end, @x,y, or a number" Is it because it wants to refer to the item number in the listbox(0, 1, 2, etc)? Not sure what's up with that or how I could get around it.

Maybe there is another way to accomplish a resume feature that I haven't thought of?

2) As I mentioned, a log file with each students name and clock in/out time is created when the buttons are pressed. I would like these logs to look a bit better by actually showing how many hours and minutes that they have been present. For example, our school hours are from 8-2:30, and each student is here for 6 hours a day (take out lunch and breaks) for our attendance records. I would like the logs to say:
John Doe Clocked in at 8:00 Clocked out at 1:00 Present for 4.5 hours
Each time that I try to look up information on how to calculate time, it's always a simple app where you have to put in the times manually. Hopefully you can see where I'm going with this.

3) If a student has not clocked in and they accidentally press the Clock Out button, it needs to show a proper error message of what they did. As of the code below, doing this action will do nothing, but console throws out an error message stating that the "tuple index out of range". Any way to correct this?


I think that's all I have right now. This app is decently solid as it stands but needs some dummy proofing. My eyes can't take any more code at the moment, thus I needed some opinions and advice. TIA!

```
from Tkinter import *
from sets import Set
import tkMessageBox
import tkFileDialog
import datetime

now = datetime.datetime.now()
filename1 = datetime.datetime.now().strftime("%m%d%Y") + '.txt'
presentStudents = list([])
absentStudents = list([])
verNum = "1.3"
resumeBefore = False
clockedIn = False

class App:
        def __init__(self, master):

                self._master = master
                frame1 = Frame(master)
                frame2 = Frame(master)
                frame1.grid(row=0, column=0)
                frame2.grid(row=0, column=1)
                
                self.value = None

                #Define the scrollbars
                stuScrollbar1 = Scrollbar(frame1)
                stuScrollbar2 = Scrollbar(frame1)

                self.aStuLabel = Label(frame1, text="Available Students")
                self.aStuLabel.grid(row=0, column=0)

                self.pStuLabel = Label(frame1, text="Present Students")
                self.pStuLabel.grid(row=0, column=2)

                #Define the All Student ListBox and set the scrollbar to the right
                self.aStuLB = Listbox(frame1, selectmode=SINGLE, yscrollcommand=stuScrollbar1.set)
                stuScrollbar1.config(command=self.aStuLB.yview)
                stuScrollbar1.grid(row=1, column=1, sticky='NS')
                self.aStuLB.grid(row=1, column=0)

                #Define the Present Student ListBox and set the scrollbar to the right
                self.pStuLB = Listbox(frame1, selectmode=SINGLE, yscrollcommand=stuScrollbar2.set)
                stuScrollbar2.config(command=self.pStuLB.yview)
                stuScrollbar2.grid(row=1, column=3, sticky='NS') 
                self.pStuLB.grid(row=1, column=2)

                #Define the clock in button
                ciButton = Button(frame2, text="Clock In", command=self.clockIn)
                ciButton.grid(row=0, column=0)

                #Define the clock out button
                coButton = Button(frame2, text="Clock Out", command=self.clockOut)
                coButton.grid(row=1, column=0)

                #Define the exit button
                exitButton = Button(frame2, text="Exit", command=frame1.quit)
                exitButton.grid(row=2, column=0)

                #Define the menubar and options
                menubar = Menu(self._master)
                helpMenu = Menu(menubar, tearoff=0)
                helpMenu.add_command(label="Resume from Crash", command=self.resume)
                helpMenu.add_command(label="About", command=self.showAboutBox)
                filemenu = Menu(menubar, tearoff=0)
                filemenu.add_command(label="Open Student File", command=self.file_open)
                filemenu.add_command(label="Exit", command=frame1.quit)
                menubar.add_cascade(label="File", menu=filemenu)
                menubar.add_cascade(label="Help", menu=helpMenu)
                self._master.config(menu=menubar)

                        
                # Automatically populates the listbox from 'students.txt', and adds all students to the 'absentStudents' list
                filename = open("students.txt")
                for line in filename:
                        line = line.rstrip('\n')
                        self.aStuLB.insert(END,line)
                        absentStudents.append(line)
                print absentStudents
                

        #Opens a file using the open file dialog box
        def file_open(self):
                filename = tkFileDialog.askopenfilename()
                with open(filename,'r') as f:
                        for line in f:
                                self.aStuLB.insert(END,line)

        #Function for clocking in
        def clockIn(self):
                now = datetime.datetime.now()
                self.value = self.aStuLB.curselection()[0]
                stuName = self.aStuLB.get(self.value)
                print stuName

                if stuName in absentStudents:
                        #Add student to presentStudents list, move student from Total Student ListBox to Present Student ListBox, and pop up information box
                        try:
                                presentStudents.append(stuName)
                                absentStudents.remove(stuName)
                                self.pStuLB.insert(END,stuName)
                                self.aStuLB.delete(self.value)
                        except:
                                print "Error:  Cannot move student"
                                
                        #Write to log file and to resume backup file
                        try:
                                f = open(filename1, 'a')
                                f.write(stuName + "\n" + "Clock In at " + now.strftime("%a - %m-%d-%y %H:%M") + "\n")
                                f.close()
                        except:
                                tkMessageBox.showinfo("Error", "Can't write to log")
                                pass

                        try:
                                f = open('resume.txt', 'a')
                                f.write(stuName + "\n")
                                f.close()
                        except:
                                print "Cannot write to resume log!"
                                pass
                elif stuName in presentStudents:
                        tkMessageBox.showinfo("Error", "You must clock in first!")

                else:
                        tkMessageBox.showinfo("Error", "General Error")

                #Show Clock In Message
                tkMessageBox.showinfo("Clocked In", "You have clocked in at " + now.strftime("%H:%M"))

        #Function for clocking out
        def clockOut(self):
                now = datetime.datetime.now()
                self.value = self.pStuLB.curselection()[0]
                stuName = self.pStuLB.get(self.pStuLB.curselection()[0])
                if stuName in presentStudents:
                        #Write to log file
                        try:
                                f = open(filename1, 'a')
                                f.write(stuName + "\n" + "Clock Out at " + now.strftime("%a - %m-%d-%y %H:%M") + "\n")
                                f.close()
                        except:
                                tkMessageBox.showinfo("Error", "Can't write to log")
                                pass


                        #Remove student from presentStudents list, move student from Present Student ListBox to Total Student ListBox, and pop up information box
                        try:
                                presentStudents.remove(self.pStuLB.get(self.value))
                                for item in presentStudents:
                                        print item
                                self.aStuLB.insert(0,self.pStuLB.get(self.value))
                                self.pStuLB.delete(self.value)
                        except:
                                print "Error:  Cannot move student"
                        
                        tkMessageBox.showinfo("Clocked Out", "You have clocked out at " + now.strftime("%H:%M"))
                else:
                        tkMessageBox.showinfo("Error", "You have not clocked in yet!")
                        pass


        def showAboutBox(self):
                #Show the About Dialog Box w/Information
                top2 = Toplevel()
                top2.title("About TCAT Timeclock")

                Label(top2, text="TCAT Timeclock App v" + verNum).pack()
                aboutOkButton = Button(top2, text="OK", command=top2.destroy).pack()

        def resume(self):
                #Resume from accidental close out or crash
                print resumeBefore
                if resumeBefore == True:
                        tkMessageBox.showinfo("You have already resumed your last session.")
                        pass
                #resumeBefore = True
                filename = open("resume.txt")

                #Read in names from 'resume.txt' into presentStudents list, then remove them from absentStudents list
                for line in filename:
                        line = line.rstrip('\n')

                        presentStudents.insert(0, line)
                        print "Present Students: \n"
                        print presentStudents
                        print "\n"
                        #absentStudents.remove(line)
                        print "Absent Students: \n"
                        print absentStudents

                        self.pStuLB.insert(END,line)
                        self.aStuLB.delete(line)

                #Insert presentStudents into pStuLB
                for line in presentStudents:
                        self.pStuLB.insert(END,line)


root = Tk()
root.title("TCAT Timeclock v" + verNum)

# Definition to center window when launching
def center_window(w=300, h=200):
        ws = root.winfo_screenwidth()
        hs = root.winfo_screenheight()
        x = (ws/2) - (w/2)
        y = (hs/2) - (h/2)
        root.geometry('%dx%d+%d+%d' % (w, h, x, y))


app = App(root)
center_window(475, 275)
root.mainloop()
```

---

### Post by micahpage on 2013-06-30
As to 1) not sure off hand. I believe you are looking for
```
        ind = self.listbox.curselection()
        selection = self.listbox.get(ind)
```. Where the first gets the index, and the second gets the selection from the index. But read here [for more info http://effbot.org/tkinterbook/listbox.htm]("http://effbot.org/tkinterbook/listbox.htm")

2) regarding time, i would do something like this:
```
import time
import datetime

clockin_stamp = time.time()
clockin_display = datetime.datetime.fromtimestamp(clockin_stamp).strftime('%H:%M')
time.sleep(3)
clockout_stamp = time.time()
clockout_display = datetime.datetime.fromtimestamp(clockout_stamp)
diff = clockout_stamp - clockin_stamp

diff_disp = time.strftime('%H:%M:%S', time.gmtime(diff))

print('clocked in at: {}'.format(clockin_display))
print('clocked out at: {}'.format(clockout_display))
print('time logged in: {}'.format(diff_disp))
```
the clockin uses strftime to just get hour and minute while the clockout doesnt, which gets everything. The time.sleep(3) is to signify the time the person is logged in. 

3)since you know it causes a tuple out of range error, you can put in a try except there
```
try:
    self.value = self.pStuLB.curselection()[0]
except IndexError:
    tkMessageBox.showerror('Error', 'You are not logged in')
    return
```

as for saving data, i wouldnt use text files. I would use a nested dictionary and in it put, student name, log in time timestamp, log out timestamp, time logged in, etc. for each student. Then use the pickle module to save it to disk. Or if using a lot of student files, maybe shelve modules instead. Or even JSON it. Any of those, save it to disk, then load it back. then index the disctionary's keys and values to get the data, then display it to program.

---

