---
title: "IMAP - Thunderbird v. 2 and Gmail working in Linux Ubuntu 9.10 &amp; FETCHed Error fixed"
date: 2009-11-20
forum: Outdated Tutorials &amp; Tips
---

### Post by specialk1st on 2009-11-20
OK, so after my day and a half long struggle to get Thunderbird (version 2.0.0.23) to work perfectly in Ubuntu 9.10 I figured I should share my knowledge and my references.

Sorry if this tutorial is really explanatory, but I want to try to help out all the beginners along with the more advanced crowd.  (I'm somewhat more advanced, but the tutorials that I found were so non-explanatory that I'm gonna try to be different.) :D ;)

Anyway, here we go... 

**How To make Mozilla Thunderbird version 2.0 and Gmail work with IMAP in Linux Ubuntu 9.10 and fix the FETCHed Error Message** 


[LIST=1]
[*]After downloading and installing Thunderbird via the "Ubuntu Software Center" in Ubuntu, launch Mozilla Thunderbird.
[*]Log onto your Gmail account using your internet browser.
[*]Then go to: [http://mail.google.com/support/bin/answer.py?answer=77662](http://mail.google.com/support/bin/answer.py?answer=77662)
[LIST]
[*]_Note:_ Step 2 in the link above is wrong.  To access the "Account Settings dialog box in Thunderbird version 2.0, you actually need to go to: Edit -> Account Settings
[*]_Note:_ Skip step 21 for now and don't change to any "Recommended Client Settings" given by Gmail.  (You can do this later, for now the basic settings to get this working are all that are needed.)
[/LIST]
 
[*]Follow the instructions there to set up your Gmail online web account and to set up Thunderbird to connect to Gmail online via IMAP.
[LIST]
[*]_Note:_ That's 2 parts - first enable IMAP in your web account then set up IMAP in your Thunderbird application (**in that order**).
[/LIST]
 
[*]After you have set up your Thunderbird account it should automatically begin to download your mail messages. (Don't worry it is only downloading the subject line not the actual messages so you aren't eating up your hard drive space.)
[LIST]
[*]_Note:_ If there is nothing being downloaded you may have to click the "Get Mail" button at the top left corner of your Thunderbird window.
[/LIST]
 
[*]If the download completes and you see all your message without an error message everything worked fine,
[LIST]
[*]**_But_,** if you get the following error message:  "The current command did not succeed. The mail server responded: Some messages could not be FETCHed (Failure)." see the instructions to fix it below...
[/LIST]
 
[/LIST]

[U][B]Problem:
[/B][/U]Mozilla Thunderbird gives you this alert when you try to download your messages to the application.[B]
Alert:  "The current command did not succeed. The mail server responded: Some messages could not be FETCHed (Failure)."[/B]

_**The Fix:**_

[LIST=1]
[*]Close Thunderbird and log out of Gmail online.
[*]Go to: Applications -> Accessories -> Terminal
[*]Enter:[SIZE=1] ***sudo cp -p /etc/profile /etc/profile_backup***[/SIZE]
[LIST]
[*][SIZE=1][FONT=Verdana]This will back up your profile, just in case you need to undo the changes below.[/FONT][/SIZE]
[/LIST]
 
[*]Next open the file in the gedit application by typing: ***gksudo gedit /etc/profile***
[LIST]
[*]A gedit window should open up.
[/LIST]
 
[*][SIZE=2][FONT=Verdana][SIZE=1]In the window that opens up, scroll down to the bottom of the text, hit the "Enter" button on your keyboard twice and type the following (on 2 separate lines in the order shown):  
[/SIZE][/FONT][/SIZE]
[LIST]
[*][SIZE=2][FONT=Verdana][SIZE=1][I][B]NSPR_LOG_MODULES=imap:5
NSPR_LOG_FILE=/tmp/imap.log[/B][/I][/SIZE][/FONT][/SIZE]
[/LIST]
 
[*][SIZE=2][FONT=Verdana][SIZE=1]Hit the "Enter" button on your keyboard twice more.[/SIZE][/FONT][/SIZE]
[*][SIZE=2][FONT=Verdana][SIZE=1]Save the file and close it.[/SIZE][/FONT][/SIZE]
[*][SIZE=2][FONT=Verdana][SIZE=1]Go back to your Terminal window, which should still be open, and type (exactly):[/SIZE][/FONT][/SIZE]
[LIST]
[*][SIZE=2][FONT=Verdana][SIZE=1]***export NSPR_LOG_MODULES=imap:5***[/SIZE][/FONT][/SIZE]
[/LIST]
 
[*][SIZE=2][FONT=Verdana][SIZE=1]Hit the "Enter" key.
[/SIZE][/FONT][/SIZE]
[*][SIZE=2][FONT=Verdana][SIZE=1]Then type (exactly):[/SIZE][/FONT][/SIZE]
[LIST]
[*][SIZE=2][FONT=Verdana][SIZE=1]***export NSPR_LOG_FILE="/tmp/imap.log"***[/SIZE][/FONT][/SIZE]
[/LIST]
 
[*][SIZE=2][FONT=Verdana][SIZE=1]Hit the "Enter" key again.
[/SIZE][/FONT][/SIZE]
[*][SIZE=2][FONT=Verdana][SIZE=1]Then launch Mozilla Thunderbird from the Terminal by typing:[/SIZE][/FONT][/SIZE]
[LIST]
[*][SIZE=2][FONT=Verdana][SIZE=1]***mozilla-thunderbird***
[/SIZE][/FONT][/SIZE]
[/LIST]
 
[*][SIZE=2][FONT=Verdana][SIZE=1]If you have your settings defined as described in Steps 2-5 above Thunderbird should start loading the message headers again.  If not hit the "Get Mail" button as described in Step 5.
[/SIZE][/FONT][/SIZE]
[LIST]
[*][SIZE=2][FONT=Verdana][SIZE=1]Note: YOU WILL GET THE ERROR/ALERT FAILURE MESSAGE AGAIN!  THIS IS OK. ;)[/SIZE][/FONT][/SIZE]
[/LIST]
 
[*][SIZE=2][FONT=Verdana][SIZE=1]In the standard view settings of Thunderbird your message subject lines should be listed in a window at the top right of the Thunderbird window...[/SIZE][/FONT][/SIZE]
[LIST]
[*][SIZE=2][FONT=Verdana][SIZE=1]It should read: | Subject | Sender | Date | [little button with picture of a table and a down arrow] |[/SIZE][/FONT][/SIZE]
[*][SIZE=2][FONT=Verdana][SIZE=1]Click the little button on the far righthand side, and check "Order Received"
[/SIZE][/FONT][/SIZE]
[/LIST]
 
[*][SIZE=2][FONT=Verdana][SIZE=1]Then in Ubuntu go through the following menu options and open the "imap.log" file: 
[/SIZE][/FONT][/SIZE]
[LIST]
[*][SIZE=2][FONT=Verdana][SIZE=1]Places -> Computer -> [Filesystem] -> tmp -> imap.log[/SIZE][/FONT][/SIZE]
[*][SIZE=2][FONT=Verdana][SIZE=1]_Note:_ If while you are in the "imap.log" file it loads a message saying that the file has changed on the disk and asks if you want to reload it answer NO/CANCEL!
[/SIZE][/FONT][/SIZE]
[/LIST]
 
[*][SIZE=2][FONT=Verdana][SIZE=1]Scroll to the bottom of the imap.log file. 
[/SIZE][/FONT][/SIZE]
[*][SIZE=2][FONT=Verdana][SIZE=1]Press the [Ctrl+F] keys and look for the following phrase (minus the quotes):[/SIZE][/FONT][/SIZE]
[LIST]
[*][SIZE=2][FONT=Verdana][SIZE=1]"[/SIZE][/FONT][/SIZE]**NO Some messages could not be FETCHed**"
[/LIST]
 
[*][SIZE=2][FONT=Verdana][SIZE=1]Search the ENTIRE file and write down or make a note somewhere of which UID numbers are generating the error message from Step 16.[/SIZE][/FONT][/SIZE]
[LIST]
[*][SIZE=2][FONT=Verdana][SIZE=1]Here is a sample "imap.log" file to taken from [here]("http://www.google.com/support/forum/p/gmail/thread?tid=1acf74d2c4c1ed46&hl=en&fid=1acf74d2c4c1ed46000478794a8f7f7b"):[/SIZE][/FONT][/SIZE]
[*][SIZE=5][COLOR=Blue]"[/COLOR][/SIZE]1344[3f74b68]: 42a5818:imap.gmail.com:S-[Gmail]/All Mail:CreateNewLineFromSocket: * 1 FETCH (UID **77 **FLAGS (\Seen))
1344[3f74b68]: ReadNextLine [stream=266f8f8 nb=37 needmore=0]
1344[3f74b68]: 42a5818:imap.gmail.com:S-[Gmail]/All Mail:CreateNewLineFromSocket: * 2 FETCH (UID 69923 FLAGS (\Seen))
1344[3f74b68]: ReadNextLine [stream=266f8f8 nb=37 needmore=0]
...
1344[3f74b68]: 42a5818:imap.gmail.com:S-[Gmail]/All Mail:SendData: 9 UID fetch **77 **(UID RFC822.SIZE FLAGS BODY.PEEK[HEADER.FIELDS (From To Cc Subject Date Message-ID Priority X-Priority References Newsgroups In-Reply-To Content-Type)])
1344[3f74b68]: ReadNextLine [stream=266f8f8 nb=51 needmore=0]
1344[3f74b68]: 42a5818:imap.gmail.com:S-[Gmail]/All Mail:CreateNewLineFromSocket: 9 **NO Some messages could not be FETCHed** (Failure)[SIZE=5][COLOR=Blue]"[/COLOR][/SIZE]
[/LIST]
 
[*][SIZE=2][FONT=Verdana][SIZE=1]The number that you should be paying attention to and making note of is the "fetch 77" right before the "[/SIZE][/FONT][/SIZE](UID RFC822.SIZE FLAGS BODY.PEEK[HEADER.FIELDS".
[*]Without closing the "imap.log" file, go back into Thunderbird, which should be still open, and look for the _number(s)_ that you noted from the "fetch ##" in Step 19 above.
[*]Scroll through Thunderbird to find that number under the "Order Received" column from Step 14 above.
[*]Write down the time and date of the message(s) that are causing the fetch error/alert.  (_**THESE MESSAGES ARE THE PROBLEM!**_)
[*]Repeat Steps 21 & 22 until you have found all the problematic messages.
[*]Log back into Gmail web/online version (i.e. www.gmail.com) using your internet browser.
[*]Search for the bad message(s) one-by-one.
[*]Delete the bad message(s) one-by-one.
[*]Logout of Gmail web/version.
[*]Close the "imap.log" file.
[*]Close Mozilla Thunderbird.
[*]Close the Terminal.
[*]Re-launch Mozilla Thunderbird and the **problem should be fixed!**  :D :KS
[LIST]
[*]If the problem still persists, then you may need to find out the date an alternate way.  See the techie way of doing it below...
[/LIST]
 
[/LIST]

[U][B]An Alternate Way of Finding the Problem Messages:
[/B][/U][INDENT]
[LIST]
[*]These steps will replace Steps 21-23 in "The Fix" listed right above.
[/LIST]
[/INDENT]
[LIST=1]
[*]Open the Terminal window by going to: Applications -> Accessories -> Terminal
[*]Enter:
[LIST]
[*]**openssl s_client -host imap.gmail.com -port 993 -crlf**
[*]**? login *yourusername@gmail.com password***
[*]**? select "[Gmail]/All Mail"**
[*]**? fetch *77* fast**
[*]Note:  You should replace the "77" written in the command above with the number "##" from the "fetch ##" line in the imap.log file.  *(See Step 19 in "The Fix" for clarification.)*
[/LIST]
 
[*]Repeat the "? fetch" command in Step 2 until you have all the date and times of the problem messages.  (**_AGAIN, THESE ARE THE PROBLEM MESSAGES!_**)
[*]Continue on from Step 24 in "The Fix" listed above.
[/LIST]

You're done!  :popcorn:  Easy right...??  :D

---

