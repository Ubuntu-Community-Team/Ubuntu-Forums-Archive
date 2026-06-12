---
title: "Gambas Help"
date: 2010-09-14
forum: Programming Talk
---

### Post by ve3tru on 2010-09-14
Problems using Gambas 2.21
 

 

 1st off I'm not a computer programmer, my knowledge of computer programming could be written on the back of a match book. I thought Id try my luck with Gambas mainly because its free, and it seems simple.  
 OK heres my problem, I thought as my first computer program Id try my luck with a simple GUI computer backup program. Everything seems to work fine, but the shell. The program executes the shell and continues on and then crashes. I need the shell to execute and not to continue on until its done. Ive followed the shell with a wait command no luck. All that does is it waits so many seconds before continuing on, It wont wait for the shell to finish.
 Very very
 Stumped
 

 PUBLIC SUB ToggleButton1_Click()
 IF ToggleButton1.Value = TRUE THEN
 PictureBox1.Visible = FALSE
 TextLabel1.Visible = FALSE
 TextLabel2.Visible = TRUE
 TextLabel3.Visible = TRUE
 MovieBox1.Visible = TRUE
 MovieBox2.Visible = TRUE
 TextLabel4.Visible = TRUE
 WAIT 3.0
 INC Application.Busy
 SHELL "tar cvpjf backup.tar.bz2 --exclude=/proc --exclude=/lost+found --exclude=/backup.tar.bz2 --exclude=/mnt --exclude=/sys /"
                                         help me here please!!!!!
 DEC Application.Busy  
 

 TextLabel6.Visible = TRUE
 MovieBox1.Visible = FALSE
 MovieBox2.Visible = FALSE
 ToggleButton1.Visible = FALSE
 ToggleButton2.Visible = FALSE
 TextLabel1.Visible = FALSE
 TextLabel2.Visible = FALSE
 TextLabel3.Visible = FALSE
 TextLabel4.Visible = FALSE
 TextLabel6.Visible = TRUE
 MovieBox1.Visible = FALSE
 MovieBox2.Visible = FALSE
 

   
 ENDIF  
 END

---

### Post by spjackson on 2010-09-14
I have never used Gambas, but the documention [http://gambasdoc.org/help/lang/shell](http://gambasdoc.org/help/lang/shell) suggests that you append WAIT to the end of the SHELL command.
```

SHELL "tar cvpjf backup.tar.bz2 --exclude=/proc --exclude=/lost+found --exclude=/backup.tar.bz2 --exclude=/mnt --exclude=/sys /" WAIT

```Doesn't that work?

---

### Post by ve3tru on 2010-09-14
Thanks but no, it won't work, as the Shell executes it gets to a point that it pauses, as its backing up a large file, the wait command thinks the process is finished but its not.
If I give it a pause time, thats all it will do is pause for such time. With leaving the wait command open it should wait till its finished but only waits till it pauses.
I'm not even sure there is an answer to this out there.

---

### Post by ve3tru on 2010-09-14
got the wait command to work finally, I think there was and extara space or something not sure but...
I got a new problem, as the shell executes the screen (the main forum that I still want running)starts to dim I guess as it pulls all the resources how do i stop it from doing that.
Tnx

---

