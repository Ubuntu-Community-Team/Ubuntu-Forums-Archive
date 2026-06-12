---
title: "run command in terminal"
date: 2013-06-05
forum: New to Ubuntu
---

### Post by menieta on 2013-06-05
Hi people I am new to ubuntu and am struggling with the run command in terminal. I have downloaded tpdebrick-v004 I got no option to run the program only extract it which i did now each time i try to run it i get the msg command not found..........please can someone help

---

### Post by vadimkolchev on 2013-06-05
Hello and welcome!
After you exctracted your program you have to change directory in terminal where your program is unpacked and run it like this  ./your_program_executable
You can't run it from terminal just by typing its name because it is not installed.

---

### Post by menieta on 2013-06-07
[FONT=Roboto, helvetica, arial, sans-serif][COLOR=#282828]Hi Firstly thank you so much for replying....these are the instructions I followed all went well until number 17. got msg command not found so skipped to 18. file unzipped successfully, well i think it did i had to put in my password and then line after line of data appeared so i assume the file was unzipped i then went to 19. and again got the msg command not found. I am all new to this so am struggling and would appreciate your input on what i could try next. many thanks [/COLOR][/FONT]
[COLOR=#282828][FONT=Roboto]6. Download the webOS 3.0.5 doctor from the URL:[/FONT][/COLOR]
[http://downloads.hel...05hstnhwifi.jar]("http://downloads.help.palm.com/webosdoctor/rom/touchpad/p305rod01122012/wd305wifi/webosdoctorp305hstnhwifi.jar")
[COLOR=#282828][FONT=Roboto]7. Select "Save File"[/FONT][/COLOR]
[COLOR=#282828][FONT=Roboto]8. Click OK[/FONT][/COLOR]
[COLOR=#282828][FONT=Roboto]9. Download tpdebrick-v004 from the URL:[/FONT][/COLOR]
[http://goo.im/devs/j...ebrick-v004.zip]("http://goo.im/devs/jcsullins/tpdebrick/tpdebrick-v004.zip")
[COLOR=#282828][FONT=Roboto]10. Select "Save File"[/FONT][/COLOR]
[COLOR=#282828][FONT=Roboto]11. Click OK[/FONT][/COLOR]
[COLOR=#282828][FONT=Roboto]12. Wait for downloads to complete[/FONT][/COLOR]
[COLOR=#282828][FONT=Roboto]13. Click "Dash Home" (icon in top left corner of screen)[/FONT][/COLOR]
[COLOR=#282828][FONT=Roboto]14. Type in "Terminal"[/FONT][/COLOR]
[COLOR=#282828][FONT=Roboto]15. Click on the "Terminal" icon[/FONT][/COLOR]
[COLOR=#282828][FONT=Roboto]16. Click in the "Terminal" window[/FONT][/COLOR]
[COLOR=#282828][FONT=Roboto]17. Run "cd Downloads"[/FONT][/COLOR]
[COLOR=#282828][FONT=Roboto]18. Run "unzip tpdebrick-v004"[/FONT][/COLOR]
[COLOR=#282828][FONT=Roboto]19. Run "cd tpdebrick-v004"[/FONT][/COLOR]
[COLOR=#282828][FONT=Roboto]20. Connect touchpad[/FONT][/COLOR]
[COLOR=#282828][FONT=Roboto]21. Hold Power+Home+VolDown buttons on Touchpad for 30 seconds[/FONT][/COLOR]
[COLOR=#282828][FONT=Roboto]22. Run "script" (this will capture the output of the tpdebrick process)[/FONT][/COLOR]
[COLOR=#282828][FONT=Roboto]23. Run "sudo ./tpdebrick XX" (where XX is the size of the TP: 16, 32 or 64)[/FONT][/COLOR]

[COLOR=#282828][FONT=Roboto]The tpdebrick process can take from 5 to 10 minutes (or even more[/FONT][/COLOR]
[COLOR=#282828][FONT=Roboto]if you have very slow network connection). It should end with "ALL DONE."[/FONT][/COLOR]
[COLOR=#282828][FONT=Roboto]If the process hangs for more than 5 minutes, you can abort the process[/FONT][/COLOR]
[COLOR=#282828][FONT=Roboto]by pressing Ctrl-\ (Ctrl key and key with '|' above '\').[/FONT][/COLOR]

[COLOR=#282828][FONT=Roboto]24. Run "exit" (this will stop the output capture started with 'script')[/FONT][/COLOR]

[COLOR=#282828][FONT=Roboto]25. If the 'tpdebrick' process did not end with "ALL DONE." you should[/FONT][/COLOR]
[COLOR=#282828][FONT=Roboto]upload the "typescript" file (the output capture) so that the cause[/FONT][/COLOR]
[COLOR=#282828][FONT=Roboto]of failure can be diagnosed. Regardless, it's a good idea to save[/FONT][/COLOR]
[COLOR=#282828][FONT=Roboto]this file somewhere for future analysis, if needed.[/FONT][/COLOR]

[COLOR=#282828][FONT=Roboto]26. Click icon in far right corner of screen[/FONT][/COLOR]
[COLOR=#282828][FONT=Roboto]27. Select "shutdown"[/FONT][/COLOR]
[COLOR=#282828][FONT=Roboto]28. Select "shutdown" or "reboot"[/FONT][/COLOR]

[COLOR=#282828][FONT=Roboto]29. Connect Touchpad to stock HP AC charger and allow to charge for[/FONT][/COLOR]
[COLOR=#282828][FONT=Roboto]several hours[/FONT][/COLOR]

---

### Post by vadimkolchev on 2013-06-07
This error means that there is no such directory and therefore you can't go to it. Check if you have directories Downloads and tpdebrick-v004 and see the path to them. You will have to "cd" to these directories from terminal.

---

### Post by lisati on 2013-06-07
Make sure you type in:
```
cd Downloads
```
and not:
```
cd downloads
```

Ubuntu's command line/terminal is case-sensitive, and sees a difference between the two.

---

### Post by vadimkolchev on 2013-06-07
And I suggest that you learn the basics of linux command line file system and navigation in it, as well as knowledge of how programs that are not installed on your system can be run from cli. It will give you the understanding of what you have to do.

---

### Post by Impavidus on 2013-06-07
Are you sure it said "Command not found"? Not "No such file or directory"? Because vadimkolchev's and lisati's suggestions apply if it said "No such file or directory". The "Command not found" error is given when the system doesn't know the command you gave, but as cd is a shell built-in it should never give this error, even if your system is utterly broken. In other words, you typed it the wrong way.

---

### Post by vadimkolchev on 2013-06-07
Sure, Impavidus is correct here. Please re-check the output again. There is no existing shell in linux, I think, that has no built-in cd command. It must be there, that's why your output seems not too correct. The best thing for you, if you need assistance, will be to paste step-by-step input and output, for us to be able to help you, because we cannot tell where it is your mistake and where just normal behaviour of the system.

---

