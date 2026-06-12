---
title: "Embed Terminal in Tkinter."
date: 2010-10-30
forum: Programming Talk
---

### Post by cgroza on 2010-10-30
Hello. I have created my own APT GUI so I don't have to open synaptic or type in terminal. Now when I open my program, it depends on a terminal to give the password for sudo and display output. What I want to do is to embed this terminal into a separate frame. I use Tkinter as my toolkit. I searched the internet but did not found anything that helped me.
I hope you will give me some hints.

Here is my code.


```
from Tkinter import *  #the GUI toolkit.
import tkMessageBox    #coming soon.
import os              #used to call system.
import os.path         #used to check the system path.
import time            #used to put the program to sleep.
import datetime        #used to get the current time.
import readline        #enables user to have inline editing and history.


top = Tk()
def gui():
    global mainFrame
    mainFrame = Frame(top,relief="sunken", border=1)
    mainFrame.pack(fill="x")
    Description = Label(mainFrame,text="APT-Mangager Menu:")
    Description.pack()


    mainFrame.master.title("APT-Manager v.1.5")
    installButton = Button(mainFrame,text="Install",command = install)
    removeButton = Button( mainFrame,text="Remove",command = remove)
    upgradeButton = Button(mainFrame,text ="Upgrade",command = upgrade)
    updateButton = Button(mainFrame,text = "Update",command = update)
    cleanButton = Button(mainFrame,text="Clean",command = areusure)
    fixbrokenButton = Button(mainFrame,text = "Fix Broken", command = fixbroken)
    customaptButton = Button(mainFrame,text = "Custom Command",command = customapt)
    manlogButton = Button(mainFrame,text = "Manage Log",command = manlog)
    settingsButton = Button(mainFrame,text = "Settings",command = settingsmenu)
    aptsourceButton = Button(mainFrame,text = "Manage Sources",command = mansource)
    aptsearchButton = Button(mainFrame,text = "Apt-Search", command = aptsearch)

    quitButton = Button(mainFrame,text = "Quit",command = quit)

    installButton.pack(fill = BOTH ,pady=10)
    removeButton.pack(fill = BOTH ,pady=10)
    upgradeButton.pack(fill = BOTH ,pady=10)
    updateButton.pack(fill = BOTH ,pady=10)
    cleanButton.pack(fill = BOTH ,pady=10)
    fixbrokenButton.pack(fill = BOTH ,pady=10)
    customaptButton.pack(fill = BOTH ,pady = 10)
    manlogButton.pack(fill = BOTH ,pady = 10)
    settingsButton.pack(fill = BOTH ,pady = 10)
    aptsearchButton.pack(fill = BOTH ,pady = 10)
    aptsourceButton.pack(fill = BOTH ,pady = 10)
    quitButton.pack(fill = BOTH ,pady=10)

    top.mainloop()

# Finds user's home folder.
HOMEDIR = os.path.expanduser('~')
#binds the logfile and conf file to home foler path.
logplace = HOMEDIR+'/.aptmanager.log'
configfile = HOMEDIR+'/.aptmanager.conf'
depfile = HOMEDIR+"/.depfile.dat"


#Submenu for the settings button.

def mansource():
    global eighthFrame
    eighthFrame = Frame(top)
    viewsourceButton = Button(eighthFrame,text = "View Source",command = viewsource)
    addsourceButton = Button(eighthFrame,text  = "Add Source",command = addsource)
    eighthFrame.pack()
    viewsourceButton.pack(pady = 10)
    addsourceButton.pack(pady = 10)


#reads the apt-source file and prints it to screen.
def viewsource():
    os.system("clear")
    view = open("/etc/apt/sources.list","r")

    os.system("clear")
    for line in view.readlines():
        print (line)

    eighthFrame.destroy()


def addsource():
    os.system("cd ~/aptmanage && sudo python edit_source.py")
    eighthFrame.destroy()


def areusure():
    global secFrame
    secFrame = Frame(top)
    warning = Label(secFrame,text="This will delete the apt-cache!")
    sureYes = Button(secFrame,text = "Yes",command = maintain)
    sureNo = Button(secFrame,text = "No",command = secFrame.destroy)
    secFrame.pack()
    warning.pack()
    sureYes.pack(padx = 10)
    sureNo.pack(padx = 10)
    sureYes.bind('<ButtonRelease-1>', secFrame.destroy)

    sureYes.focus_force()


def notify():
    os.system(notifycmd)


#calls apt-get install <user input>.
def install():
    os.system('clear')
    i = raw_input('Enter app name from repository: ')
    cmd="sudo apt-get install " + i+" "+logcmd
    os.system(cmd)
    insertdate()
    notify()
    print_time()


# takes user input, appends to a string and passes to bash.
def remove():
    os.system('clear')
    r = raw_input("Enter app name to remove: ")
    cmd2="sudo apt-get remove "+r+" "+logcmd
    os.system(cmd2)
    insertdate()
    notify()
    print_time()


# executes the update and upgrade command
def upgrade():
    os.system('clear')
    cmd3="sudo apt-get update "+logcmd+" && sudo apt-get upgrade "+logcmd
    os.system(cmd3)
    insertdate()
    notify()
    print_time()


# executes the update command
def update():
    os.system('clear')
    cmd4="sudo apt-get update "+logcmd
    os.system(cmd4)
    insertdate()
    notify()
    print_time()


# performs basic apt maintainance.
def maintain():
    os.system('clear')
    secFrame.destroy()

    cmd5=('sudo apt-get clean '+logcmd+" && sudo apt-get autoremove "+logcmd+ "&& sudo apt-get autoclean "+logcmd)
    os.system(cmd5)
    insertdate()
    notify()
    print_time()


# passes the input to bash.
def customapt():
    os.system("clear")
    customcmd= "sudo apt-get " + raw_input("Enter custom APT-GET command: ")
    os.system(customcmd)
    print("Done")

#calls sudo apt-cache search <user input>
def aptsearch():
    os.system("clear")
    search=raw_input("Enter search criteria: ")
    os.system("clear")
    print("The results for "+search+" are:")

    cmd6="sudo apt-cache search "+search
    os.system(cmd6)


# calls dpkg via bash to repair broken packages.
def fixbroken():
     os.system("clear")
     os.system("sudo apt-get update "+logcmd)
     os.system("sudo apt-get -f install "+logcmd)
     os.system("sudo dpkg --configure -a --force-all "+logcmd)
     notify()
     print_time()



#checks the current time and prints it on the screen.
def print_time():
     now = datetime.datetime.now()
     chour =str(now.hour)+ ":"
     cmin = str(now.minute)
     print("\nFinished at: " + chour + cmin)


# writes the current time and date at the end of the file.
def insertdate():
    #checks if the log is enabled. If yes, it continues.
    if logcmd != "":

#takes the current date and time.
        logfile = open(logplace,"a")
        now = datetime.datetime.now()

#separates them by day,hour,minute.
        cdate = "date: " + str(now.day) + " "
        chour = "hour: " + str(now.hour) + " "
        cmin = "minute: " + str(now.minute) + " \n"

#writes them at the end of the log file.
        logfile.write(cdate)
        logfile.write(chour)
        logfile.write(cmin)
        logfile.close()


#Function for the Manage Log button.
def manlog():
    global thirdFrame
    thirdFrame = Frame(top)
    os.system("clear")
    viewlogButton = Button(thirdFrame,text="View Log",command = viewlog)
    eraselogButton = Button(thirdFrame,text = "Erase Log",command = eraselog)
    thirdFrame.pack()
    viewlogButton.pack(pady = 10)
    eraselogButton.pack(pady = 10)


#sub button for the Managee Log button.
def viewlog():
 os.system("clear")
 thirdFrame.destroy()
 try:
    os.system("clear")
    logfile = open(logplace,"r")
    lfile = logfile.readlines()
    for line in lfile:
         print (line)

    logfile.close()


# handles the error in case the log file is not found.
 except IOError:
     os.system("clear")
     print("No log found.")


#sub button for the Manage Log button.
def eraselog():
   os.system("clear")
   thirdFrame.destroy()
   logfile = open(logplace,"w")
   logfile.write("")
   logfile.close()
   print ("Log file cleared.")


#Function for the Settings button.
def settingsmenu():
    global sevFrame
    sevFrame = Frame(top)
    editsettingsButton = Button(sevFrame,text = "Edit Settings",command = settings)
    installdepButton  = Button(sevFrame, text = "Install Dependency",command = installdep )
    sevFrame.pack()
    editsettingsButton.pack(pady = 10)
    installdepButton.pack(pady = 10)


#installs the required dependencyes when called.
def installdep():
    os.system("clear")
    os.system("sudo apt-get install libnotify-bin")
    sevFrame.destroy()

#sub button for the settins menu.
def settings():
    sevFrame.destroy()
    logsettings()
    notifysettings()


#sets the log preferences.
def logsettings():
    global fifthFrame
    fifthFrame = Frame(top)
    logsetyesButton = Button(fifthFrame,text = "Enable Log", command = logsetyes)
    logsetnoButton = Button(fifthFrame,text = "Disable Log",command = logsetno)
    fifthFrame.pack()
    logsetyesButton.pack(pady = 10)
    logsetnoButton.pack(pady = 10)

#called if log must be enabled.
def logsetyes():
    logcmd="| tee -a ~/.aptmanager.log"
    conf = open(configfile,"w")
    conf.write("")
    conf.close()

    conf = open(configfile,"a")
    conf.write("log=enabled\n")
    conf.close()
    fifthFrame.destroy()
    notifysetyesButton.pack(pady = 10)
    notifysetnoButton.pack(pady = 10)


#called if log must be disabled.
def logsetno():
    global notifysetyesButton
    global notifysetnoButton
    logcmd=""
    conf = open(configfile,"w")
    conf.write("")
    conf.close()

    conf = open(configfile,"a")
    conf.write("log=disabled\n")
    conf.close()
    fifthFrame.destroy()
    notifysetyesButton.pack(pady = 10)
    notifysetnoButton.pack(pady = 10)


#sets the notification preferences.
def notifysettings():
    global sixthFrame
    global notifysetyesButton
    global notifysetnoButton
    sixthFrame = Frame(top)
    notifysetyesButton = Button(sixthFrame,text = "Enable Notification",command = notifysetyes)
    notifysetnoButton = Button(sixthFrame,text = "Disable Notification",command = notifysetno)
    sixthFrame.pack()


#called if notifications must be enabled.
def notifysetyes():
    conf = open(configfile,"a")
    notifycmd ="notify-send APT-Mananger 'Operation Finished'"
    conf.write("notification=enabled\n")
    conf.write("EOF")
    conf.close()
    sixthFrame.destroy()


#called if notification must be disabled.
def notifysetno():
    conf = open(configfile,"a")
    notifycmd = ""

    conf.write("notification=disabled\n")
    conf.write("EOF")
    conf.close
    sixthFrame.destroy()


#asks the user for dependency installation.
def depntfound():
   print("A required dependency is not installed.")
   ask_user= raw_input("1 to Install It.\n2 to Continue Without It\n3 Don'nt bother Me Again.\n?1/2/3: ")

   if ask_user == "1":
       os.system("sudo apt-get install libnotify-bin | tee -a ~/.aptmanager.log")
       print("Done.")
       raw_input("Press <enter> to continue.")
       os.system("clear")


# sets the string that is passed to bash to "" to avoid command not found errors.
   if ask_user == "2" :
       notifycmd = ""
       print("APT-Manager will continue, but with out the notification system.")
       raw_input("Press <enter> to continue.")
       os.system("clear")

   if ask_user == "3":
       dep_pref = open(depfile,"w")
       dep_pref.close()
       os.system("clear")

   else:
       os.system("clear")
       depntfound()



#reads conf file and sets the respective variables.
if os.path.exists(configfile):

    conf = open(configfile,"r")
    while True:
        line=conf.readline()
        if "notification=disabled"  in line:
            notifycmd = ""

        elif "notification=enabled" in line:
            notifycmd ="notify-send APT-Mananger 'Operation Finished'"

        if "log=disabled"  in line:
            logcmd=""

        elif "log=enabled" in line:
            logcmd="| tee -a ~/.aptmanager.log"

        if "EOF" in line:
            conf.close()
            break

#creates a default conf file if it does not exists.
else :
    print("No conf file found!\nTaking Default...")
    time.sleep(1)
    notifycmd ="notify-send APT-Mananger 'Operation Finished'"
    logcmd="| tee -a ~/.aptmanager.log"
    conf = open(configfile,"w")
    conf.write("")
    conf.close()

    conf = open(configfile,"a")
    conf.write("log=enabled\n")

    conf.write("notification=enabled\n")
    conf.write("EOF")
    conf.close()



#checks if "notify-send" exists in path (aka installed), if not, depntfound is executed.
for dir in os.environ['PATH'].split(':'):
        prog = os.path.join(dir, "notify-send")

        #checks if depfile.dat exists in home folder.
        if os.path.exists(depfile):
            notifycmd = ""
            os.system("clear")
            gui()

        #checks if file exist (this determines if depntfound() is called.)
        if os.path.exists(prog):

            gui()

depntfound()
```

Thank you.

---

