---
title: "How-to: Screen “Crash Coarse”"
date: 2007-07-05
forum: Outdated Tutorials &amp; Tips
---

### Post by TitanKing on 2007-07-05
**Introduction:**
a Typical event, I login through SSH to my server terminal, using “ssh [EMAIL="root@example.com"]root@example.com[/EMAIL]” and get presented with my servers terminal window as usual. I start doing a distro upgrade since I did it like 6 months ago. Obviously allot of things need updating.  I start with the update process and half way down I accidentally close the terminal window. Although not a train smash in this event, it could have been ugly in another. So this is not the right way to it, however like every other problem, Linux has the answer.

**How it should be:**
This is how it should be, just like above you login to your server, but you create a session, you run your update inside that session to finish. You close your terminal and exit switch of your pc and go home. At home you login and also login to your server, you now want to see what the progress is on your server that you ran in the above mentioned session. You login to that session and see exactly the screen as you last seen on your server the first time you logged in with the exception of the progress meter that advanced. 

This is what the jewel called “screen” does! Can't live without it.

Very useful even on local machine.

**How to use it:**
I prefer to create one screen session per server and rather have multiple terminals open in that session otherwise it starts getting messy.

**Creating a session:**
To create a session is a simple process, you will either want to name your session or use the auto naming.

***Method 1:*** Default naming scheme
```
screen
```[B][I]

Method 2:[/I][/B] Custom name
```
screen -S mysession
```After you used either one method, a session is now created. If you repeat this process another session will get created, you don't need this very often except if multiple users will work on the server at the same time. For now we keep it simple with 1 session and multiple windows inside it.

**Checking available sessions:**
At some point you would want to know what sessions is available for you to access. 

*Typing this:*
```
screen -ls
```

*Prints out:*
```
There is a screen on:

        4126.mysession  (Attached)

1 Socket in /var/run/screen/S-jason.
```Ah so my session is created. And I am attached to this session already because I created it just now.

**Opening new windows in my session:**
Because you are currently in your session already you can start creating new windows/”terminal screens” inside your session.

Lets open a few.
Because you are already in an empty terminal window we will just type something in this terminal it will usually be a command but we are just feeling ground here. 

* So lets type something like:*
```
echo “Hello Terminal 1”
```...and press enter.

Lets create a second terminal window:
*Press:*
```
[Ctrl] + a + c
```You will now be presented with a new terminal window which is your second terminal window.

*Again type something like:*
```
echo “Hello Terminal 2”
```...and press enter.

Now you have 2 terminals open in 1 session. You can have as many terminals as you like.

```
Switching between terminals:
```You obviously need a way to find your existing terminals again.

To switch back and forth between your terminal windows use:
```
[Ctrl] + a + n
```*And*

```
[Ctrl] + a + p
```*Or you can even do this to find terminal 1:*

```
[Ctrl] + a + 1
```*terminal 2:*

```
[Ctrl] + a + 2
```Detach a session to resume with it later:
Ok you are now at that stage where you want to do something else so you want to detach from the session, it will run in the background, you just want to resume with whatever on a later stage or from another PC.

**To detach from a session press:**
```
[Ctrl] + a + d
```Now, test it by closing your terminal completely. .............imagine you were away for 5 hrs now and you are in the mood to resume with whatever you were doing.

So open your terminal (SSH to server if the test was done on another pc) and 
[I]
type:[/I] 
```
screen -ls
```*This prints out on my pc:*
```
There is a screen on:

        4126.mysession  (Detached)

1 Socket in /var/run/screen/S-jason.
```**Connecting to old session:**
Ok lets connect to above mentioned session.

*type:*
```
screen -r 4126
```*Note that I used my id before “.mysession” yours will be different most probably. 

There you go you are now reconnected to your old session and you will see your 2 terminals like you left it.

Closing the session completely:
Obviously at some point you would want to close the session completely when you are finished with what ever you are doing, this will destroy the session completely. You will not be able to access it any more.

To destroy a session you will:

***Method 1:***
*Type:*
```
exit
```...in terminal windows until you are back where you started from.

***Method 2:***
*Press:*
```
[Ctrl] + [Shift] + d
```You will note, when you:
```
screen -ls
```no sessions will show!

No Sockets found in /var/run/screen/S-jason.


**Many more functions:**
There are many more functions that make screen extremely powerful.

*type:*
```
man screen
```To see a list of advanced features.

**Other detailed tutorial:**
Here is a more advanced tutorial:
[http://www.bangmoney.org/presentations/screen.html](http://www.bangmoney.org/presentations/screen.html)

**Conclusion:**
Now think of the possibilities. Weather you admin a server, working on your localhost this could be some serious tool. Its part of my life, make it part of yours to simplify things forever!

---

