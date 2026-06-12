---
title: "Need to create a menu based shell script but i keep getting problems ???"
date: 2014-05-19
forum: New to Ubuntu
---

### Post by shon2 on 2014-05-19
There are two parts i have to do , first part is create a menu based script name "  " with ID number which will display ten menu options .
It is in a table though i will write in like a line .

Menu Tag     Menu Item         The function it does on menu selection

A                File content of       It should display the contents of /etc/group file in a dialog textbox with the current date and time at the top of the windows.
                  /etc/group

B                File content of       It should display the contents of /etc/fstab file in a dialog textbox with the current date and time at the top of the windows.
                  /etc/fstab

C               File content of      It should display the contents of  $HOME/.bashrc file in a dialog textbox with the current date and time at the top of the windows
                 $HOME/.bashrc

d.              File content of       It should display the contents of  /etc/mtab  file in a dialog textbox with the current date and time at the top of the windows
                 /etc/mtab

e.              Directory content    It should display the list of all files and directories of  /etc/skel in a dialog textbox with the current date and time at the top of the windows
                 /etc/skel

f.              File content of         It should display the contents of /etc/passwd file in a dialog textbox with the current date and time at the top of the windows
                /etc/passwd

g. File content of ithould display the contents of  /etc/profile file  in a dialog textbox with the current date and time at the top of the windows
               /etc/profile 

H.            File content of 
               ~/.bash_logout           It should display the contents of  ~/.bash_logout  in a dialog textbox with the current date and time at the top of the windows

I .           Directory content  of  /etc/pam.d   

It should display the contents of the directory /etc/pam.d in a dialog textbox with the current date and time  and count of files /scripts under                                                this directory at the top of the window
            

Exit         Exit from this menu       It should end the  program      



So pretty much this is the first part i have to do , the first one i did came with with an error then i kept trying in different ways to solve , still no luck . Then i thought to post it on here , hopefully someone can help me out here please , i do get it but somehow i can't figure out the answer , so please help . Thanks

Please Note: It is like this just so you don't get confused each line is File content of /etc/group -This is an example followed by It should display

---

### Post by steeldriver on 2014-05-19
Hello and welcome to the forums

What did you try exactly, and what were the errors? We aren't a homework service - we're happy to give hints and help you troubleshoot if you post a specific question demonstrating that you have made a genuine effort to complete the assignment, but just posting your assignment will get the thread closed.

---

### Post by shon2 on 2014-05-19
sorry steel driver - i did have try more than once , say for the first one i tried - writing it and got an error , for some reason i can past it from text editor to over here , i will post this in  here  for  what i wrote in another 7 hours . One thing to know is i have latest linux installed and the very first error was , error expected a box option but nothing is seen and another thing is whole code/script when wrote in command terminal , and pressed enter , nothing happens , no answer . so if someone out there who knows about this , plz can u help me out , u can also pm in here i believe . Thanks

---

### Post by shon2 on 2014-05-20
So here is what i wrote and what takes me to an error in terminal or basically nothing happens. This is for the first one [COLOR=#000000]File content of [/COLOR][COLOR=#000000]/etc/group .  If anyone could please look and help me out so i can try do the rest .[/COLOR]
```

[COLOR=#000000]#!/bin/bash[/COLOR]
[COLOR=#000000]# utilitymenu.sh[/COLOR]
[COLOR=#000000]# Store menu options selected by the user [/COLOR]
[COLOR=#000000]INPUT=/tmp/menu.sh.$$[/COLOR]

[COLOR=#000000]#Storage file for displaying cal and date command output[/COLOR]
[COLOR=#000000]OUTPUT=/tmp/output.sh.$$[/COLOR]

[COLOR=#000000]# get text editor or fall back to vi_editor[/COLOR]
[COLOR=#000000]vi_editor=${EDITOR-vi}[/COLOR]

[COLOR=#000000]# trap and delete temp files[/COLOR]
[COLOR=#000000]trap  "rm $OUTPUT; rm $INPUT; exit" SIGHUP SIGINT SIGTERM[/COLOR]

[COLOR=#000000]#[/COLOR]
[COLOR=#000000]#Purpose  - display output using msgbox[/COLOR]
[COLOR=#000000]# $1    -> set msgbox height[/COLOR]
[COLOR=#000000]# $2    -> set msgbox width[/COLOR]
[COLOR=#000000]# $3    -> set msgbox title[/COLOR]
[COLOR=#000000]#[/COLOR]
[COLOR=#000000]function display_outout() {[/COLOR]
[COLOR=#000000]           local  h=${1-10}                  #  box height default 10[/COLOR]
[COLOR=#000000]           local  w=${2-41}          # box width default 41[/COLOR]
[COLOR=#000000]           local  t=${3-Output}     # box title [/COLOR]

[COLOR=#000000]          dialog --backtitle "             " --title "${t}" --clear --msgbox  "$(<$OUTPUT)" ${h} ${w}[/COLOR]
[COLOR=#000000]}[/COLOR]
[COLOR=#000000]#[/COLOR]
[COLOR=#000000]# Purpose - display  current system date & time [/COLOR]
[COLOR=#000000]#[/COLOR]
[COLOR=#000000]function  show_date(){[/COLOR]
[COLOR=#000000]           echo "Today is $(date)  @ $ (hostname -f)." > $OUTPUT[/COLOR]
[COLOR=#000000]    display_output 6 60 "Date and Time"[/COLOR]
[COLOR=#000000]}[/COLOR]
[COLOR=#000000]#[/COLOR]
[COLOR=#000000]# Purpose - display a calendar[/COLOR]
[COLOR=#000000]#[/COLOR]
[COLOR=#000000]function show_ calendar () {[/COLOR]
[COLOR=#000000]           cal >$OUTPUT[/COLOR]
[COLOR=#000000]           display_output 13 25 "Calendar"[/COLOR]
[COLOR=#000000]}[/COLOR]
[COLOR=#000000]#[/COLOR]
[COLOR=#000000]# set infinite loop[/COLOR]
[COLOR=#000000]#[/COLOR]
[COLOR=#000000]while true[/COLOR]
[COLOR=#000000]do[/COLOR]

[COLOR=#000000]### display main menu ###[/COLOR]
[COLOR=#000000]dialog --clear --help-button -backtitle "Main Menu" \[/COLOR]
[COLOR=#000000]--title "[MAIN -MENU]" \[/COLOR]
[COLOR=#000000]--menu "You can use the  UP/DOWN arrow keys , the first \n\[/COLOR]
[COLOR=#000000]letter of the choice as a hot key, or the  \n\[/COLOR]
[COLOR=#000000]number keys 1-9 to choose an option . \n\[/COLOR]
[COLOR=#000000]Choose the TASK" 15 50 4 \[/COLOR]
[COLOR=#000000]Date /time "Displays date and time" \[/COLOR]
[COLOR=#000000]Calendar   "Displays a calendar" \[/COLOR]
[COLOR=#000000]Editor      "Start a text editor "\[/COLOR]
[COLOR=#000000]Exit         "Exit to the shell " 2> "${INPUT}"[/COLOR]

[COLOR=#000000]menuitem=$(<"${INPUT}")[/COLOR]

[COLOR=#000000]# make decision[/COLOR]
[COLOR=#000000]case $menuitem in[/COLOR]
[COLOR=#000000]          Date/time) show _date ;;[/COLOR]
[COLOR=#000000]          Calendar)   show _calendar;;[/COLOR]
[COLOR=#000000]          Editor)  $vi_editor;;[/COLOR]
[COLOR=#000000]          Exit )  echo "Bye"; break;;[/COLOR]
[COLOR=#000000]esac[/COLOR]

[COLOR=#000000]done[/COLOR]

[COLOR=#000000]# if temp file found , delete em[/COLOR]
[COLOR=#000000][-f  $OUTPUT ] && rm $OUTPUT[/COLOR]
[COLOR=#000000][-f  $INPUT  ]   && rm $INPUT[/COLOR]

```

[COLOR=#000000]Then says  save and close the file. Run it as follows [/COLOR]
```
 [COLOR=#000000]chmod +x utilitymenu.sh.[/COLOR]
```[COLOR=#000000]

when i run it thats where error or sometime nothing happens , plz if anyone can advise me anything , i will appreciate it .Thanks[/COLOR]

---

### Post by m1qkus on 2014-05-20
Works in priciple. You just have a couple of typos. You don't see the error messages because of the loop. 
Line 38: should be show_calendar, without a space. Same for lines 64 and 65
Line 49:: should be --backtitle with 2 dashes. 
That will at least bring up the dialog. Try using the commands outside of the script to see what goes wrong. 

Best,
m1qkus

---

### Post by shon2 on 2014-05-20
Thanks m1qkus ,  I tried , no luck meaning there was no dialog box seen , only thing seen is I copy it from text editor to terminal , paste it and run it , and so then nothing is seen , just what I pasted is seen , do you think my code needs to be changed if yes can you please let me know which one I could use , thanks for help by the way once again.

---

### Post by steeldriver on 2014-05-20
I've added CODE tags to make it easier for people to read and comment on your code.

Meantime, can you post EXACTLY how you are running the script and EXACTLY what error you are getting? Saying "[COLOR=#000000]when i run it thats where error or sometime nothing happens" doesn't help us much.[/COLOR]

---

### Post by shon2 on 2014-05-20
Thanks steeldriver , I will now tell you exactly what I do to run the script first , I grab the "whatever " script I have written , from text editor in latest Linux version , then past it on terminal and run it , now the error which I usued to get in first place was 'EXPECTED a box option'  but than on the right side -Error message seen , now when I changed some code in  scripts  ,error message seem to have gone but when I paste the whole code/script in terminal , and press enter , there is no dialog box seen meaning tells me "something is wrong maybe the code or space is missing or any other thing is missing to run the script  , that's why I asked [**[COLOR=#000000]m1qkus[/COLOR]**]("http://ubuntuforums.org/member.php?u=1855386") who tried to help me out , shall I change the code or what and the person hasn't replied yet . So steel drive , do you know anyone over here who can help me out here , or point me a direction where I can get things sorted .I hope you understand what im saying  , thanks

---

### Post by steeldriver on 2014-05-20
I'm sorry, I don't really understand what you are saying

But pasting the text into a terminal isn't really how you should be running the code - you should **save** the file, then run the **chmod** command that you mentioned in your previous post, then run it from the terminal by **changing to** the directory that contains the file, then typing the **filename** preceded by **./** (for current directory) e.g.

```

chmod +x utilitymenu.sh

./utilitymenu.sh

```

As m1qkus already mentioned, you will (at a minimum) need to remove the spaces from your function names e.g. 

```

function [COLOR=#ff0000]show _calendar[/COLOR] () {
           cal >$OUTPUT
           display_output 13 25 "Calendar"
}

```

That should at least get you to the point where the menu pops up - and you can start to debug the functionality from there

---

### Post by QIII on 2014-05-20
Hello!

May I ask why you are doing this?

---

### Post by shon2 on 2014-05-21
> **steeldriver said:**
> I'm sorry, I don't really understand what you are saying

But pasting the text into a terminal isn't really how you should be running the code - you should **save** the file, then run the **chmod** command that you mentioned in your previous post, then run it from the terminal by **changing to** the directory that contains the file, then typing the **filename** preceded by **./** (for current directory) e.g.

```

chmod +x utilitymenu.sh

./utilitymenu.sh

```

As m1qkus already mentioned, you will (at a minimum) need to remove the spaces from your function names e.g. 

```

function [COLOR=#ff0000]show _calendar[/COLOR] () {
           cal >$OUTPUT
           display_output 13 25 "Calendar"
}

```

That should at least get you to the point where the menu pops up - and you can start to debug the functionality from there



Thanks Steeldriver , I got the same thing you said from someone today , so thanks to you also

---

