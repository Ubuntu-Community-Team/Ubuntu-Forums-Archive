---
title: "TCL/EXPECT: switch between user crontrol and the script on the fly?"
date: 2009-03-24
forum: Programming Talk
---

### Post by qmqmqm on 2009-03-24
I am using Expect scripts for automation. Sometimes the question prompts change - which means sometimes my existing Expect script would hang, and I need to go into the expect script and make it match the questions again, and re-run it.

Since this happens quite oftenly, I wonder if there is a way to switch between user input and the expect script on the fly - meaning I can get user control any time I want when the script hangs, then after I manually enter some inputs I can hand the control back to the script any time I want.

I know the command "interact" can acheive this, however it seems like you have to know exactly where you want to interrupt the script.

Any ideas?

Thanks,

Tom

---

### Post by qmqmqm on 2009-04-30
I think I have found some answer here:

[http://www.wellho.net/forum/The-Tcl-programming-language/Exiting-from-interact-Expect.html](http://www.wellho.net/forum/The-Tcl-programming-language/Exiting-from-interact-Expect.html)

> interact is used to provide a "pipe" through your application from your keyboard to the system / process to which you've established contact; apart from anything specified when you start your intereact command, it's going to pass through and pass back anything that you type or the remote process generates.   In other words, you need to tell interact how it's to exit before you start it running, and it will monitor for that string.

For example:

interact +++ return
will start interact, and it will continue providing the connection to you until a stream of three "+" characters is encountered ... at which time it will return to your Expect script which will carry on.

If you wish to have your interact return to you on the completion of an ftp operation, you could use
interact ftp> return

The -o option to interact allows you to specify an EOF action - i.e. what interact is to do if the remote process terminates or drops the connection, and this can include a return ... although if you don't specify it, it's added by default anyway (after all, what else could interact do?)
interact -o eof return


Posted by bharaniks (bharaniks), 3 May 2005
Hi Graham Ellis,

I really Thankyou a lot, for the help and sorry 
to disturb you again.

One more query, i've dropped the script file in path
/usr/bin and given permission as 750 thats the root
has "7", group users has "5" and other users has "0"
now the user can execute the script, right.

But also the user can view the file by 
"cat /usr/bin/script" but the user should not view the 
file and only they should execute the script.

I belive that if the permission is set only to "1" 
then the user cannot execute the script.

Kindly help me on this regards.

Thanksyou once again.
- Bharani


Posted by admin (Graham Ellis), 3 May 2005
The "x" permission bit is used to control whether a script can be executed and the "r" permission bit to control whether it's readable.  If you were to attend one of my Linux courses, I would STRONGLY advise you to use the letters rather than the numbers if at all possible to set permissions ... but if you must use numbers then, yes

0 - no access
1 - execute only
4 - read only
5 - both read and execute


Posted by bharaniks (bharaniks), 3 May 2005
Hi Graham Ellis,

Thankyou for the information.

Yes, i've planned to attend a Linux course to gain a 
better knowledge but for next 4weeks its not possible
because with in a month my project should be 
completed.  Would be better if it can be started after 
a month.

For this issue how can i solve it ?

My requirement is to run the script alone but not 
to be viewed by the user. Can you please suggest 
me if there is any other option. 

Hope you will provide me a Positive result.

Regards
Bharani


---

