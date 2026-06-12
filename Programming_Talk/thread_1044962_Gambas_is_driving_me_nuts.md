---
title: "Gambas is driving me nuts"
date: 2009-01-19
forum: Programming Talk
---

### Post by Takar on 2009-01-19
Hey all,

I am working with Gambas to try and create a program to connect a bunch of other information together.  However, I haven't been able to figure out the open command.  What I would like to have happen is when I hit the button, it opens an Open Office spreadsheet which is saved on the computer.  I have already moved the spreadsheet into the program directory so Gambas sees it as being a file.  Any help would really be appreciated.

Also, is there any way to make my buttons transparent?

-Dave

---

### Post by slavik on 2009-01-20
As for making transparent buttons, I am not sure. for opening the spreadsheet in OpenOffice, you need to find out how to pass commands to the shell, then you can tell the shell to run oocalc and give the file as an argument.

---

### Post by orven_llantos on 2009-03-03
hope this post is not that too late for the problem at hand. i have created an object that can execute a command in the console. actually, i found this in the example programs of gambas and find it neat to encapsulate it as an object. the name of this object is "ProcessClass", please follow the declarations below:

PRIVATE hProc AS Process

PUBLIC SUB _new()  
  hProc = EXEC ["bash", "--noediting"] FOR WRITE  
END

PUBLIC SUB ConsoleCommand(command AS String)
   DIM msg AS String
   msg = Conv$(command & gb.NewLine, Desktop.Charset, System.Charset)
   PRINT #hProc, msg;
END

PUBLIC SUB freeProcess() 
    hProc.Close
    hProc.Kill
    hProc = NULL
END

it's quite simple and easy to use. first, declare in a module like this:

   public console as NEW ProcessClass

and you can refer to this module everytime you wanted to execute a console command inside gambas (ie, starting openoffice, firefox, etc...). for example, if the name of this module myglobals, then in an event where you wanted to execute a console command inside gambas write:

   myglobals.console.consolecommand("firefox")

this statement will start firefox. or in your case if you have copied all the file for opening with openoffice in your gambas project directory you can write:

   myglobals.console.consolecommand("openoffice.org -calc " & Application.Path &/ "filename.odt")

this should start OOCalc with the filename.odt in it.

as a finale, before the program exits you have to do this
    
   myglobals.console.freeProcess()
   myglobals.console = NULL

cheers,

orven

---

