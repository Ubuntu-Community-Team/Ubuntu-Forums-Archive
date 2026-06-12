---
title: "How to &quot;Post terminal output&quot;?"
date: 2016-12-13
forum: New to Ubuntu
---

### Post by juntjoo2 on 2016-12-13
Apparently everyone knows the answer since Google results show people asking how to PRINT terminal output. So someone is asking me this question and I'm staring at this black window I learned how to conjure up by this secret combination of keyboard keys I have burnt into the leather of my belt which apparently holds the secrets to this most powerful operating system of the known universe, allegedly, thinking I'm smart and if I repeat this print error I'm currently receiving magically a message will appear in this black window containing the answer to all my deepest questions... or just to the issue with my printer. But nothing happened. Could someone help redirect my path to ultimate knowledge and wisdom? Thanks

---

### Post by vasa1 on 2016-12-13
That question could be rephrased simply as "how do I copy terminal output to paste elsewhere". It would save everyone's time :)

I use the mouse. Left-click, drag to highlight. Right-click, paste, to paste.

---

### Post by yetimon_64 on 2016-12-13
Your question isn't particularly clear, but I think you are asking about keyboard combinations for copying and pasting. Is that right ?

If so, in all other GUI applications (other than the terminal) like your browser or a text editor etc, the combinations are; "ctrl + c" for copying, "ctrl + x" for cutting and "ctrl + v" for pasting.

But the terminal is a special case, only copy and paste work NO cut is available and the combinations are different in there, "ctrl + shift + c" for copying and "ctrl + shift + v" for pasting. 

For example if you are in a browser and highlight and copy a code string, you do so with the "ctrl + c" combination; then on opening a terminal you can put the cursor in place and use "ctrl + shift + v" to paste in what you have just copied in the browser (or any other GUI application like editors etc).

In the terminal if you highlight some code and want to copy it you use, "ctrl + shift + c" to do so and then to paste to a GUI application (like firefox for posting code to this forum) you use "ctrl + v" to do the pasting.

Just remember no cutting is available in the terminal, only copying and pasting and you use the same combination with the shift key added when in the terminal. Traditionally ctrl + c and ctrl + v have had special functions allocated to them in the terminal, so the shift key is added to give equivalent copy and pasting functionality as the rest of the GUI. 

Or as vasa1 notes you have the right click context menu available including in the terminal ;).

---

### Post by juntjoo2 on 2016-12-13
Sorry, I'm asking how to GET terminal output. Someone is asking me to post it but I don't know how to get it.

---

### Post by QIII on 2016-12-13
Hello.

Highlight the output with your mouse and then follow yetimon_64's instructions in the third paragraph above.

There is a saying that deals with flies, honey and vinegar.  Are you familiar with it?

---

### Post by yetimon_64 on 2016-12-13
> **juntjoo2 said:**
> Sorry, I'm asking how to GET terminal output. Someone is asking me to post it but I don't know how to get it.

Drag a selection over any terminal output needed so it is highlighted then use either the right click context menu (easiest option) or the key cominations and copy it. 

Then in the editor here paste it in with either the right click menu in the forum editor, or the keyboard combination mentioned earlier, between [noparse]```

```[/noparse] tags; the advance editor here has a # button on the toolbar for easier inserting of such tags.

---

### Post by wildmanne39 on 2016-12-13
Please show us the code you are posting in the terminal, I suspect you are using sudo and do not realize that after you enter a command beginning with sudo you have to type your user password but it is invisible you will not see it on the screen so once you type the user password hit enter.

---

### Post by &amp;KyT$0P# on 2016-12-13
> **juntjoo2 said:**
> Sorry, I'm asking how to GET terminal output. Someone is asking me to post it but I don't know how to get it.
You're not using XTerm or UXTerm, are you?

If not, it goes like this.  Copy their command to clipboard (right-click > Copy, or just press Ctrl-C).  Open your Terminal application.  Right-click > Paste.  Then press Enter to run the command.

It should spit something out.  That "something" is what is meant by "terminal output" and what they are asking you to post. :)

---

### Post by juntjoo2 on 2016-12-13
I'm not typing anything. Things just happen and people say "post terminal output". Right now printer isn't printing. Now I'm supposed to provide terminal output. How do you get that?

---

### Post by QIII on 2016-12-13
Would you please open a terminal, type ```
df -h
```, press enter and tell us what happens?

---

### Post by juntjoo2 on 2016-12-13
```
ben@Hal:~$ df -hFilesystem      Size  Used Avail Use% Mounted on
udev            1.8G     0  1.8G   0% /dev
tmpfs           363M   11M  352M   3% /run
/dev/sda5       100G   12G   83G  13% /
tmpfs           1.8G   21M  1.8G   2% /dev/shm
tmpfs           5.0M  4.0K  5.0M   1% /run/lock
tmpfs           1.8G     0  1.8G   0% /sys/fs/cgroup
tmpfs           363M   84K  363M   1% /run/user/1000

```

where are we going?  I just want to know what people talk about when they say "post terminal output" lol, why is this so hard.  what do you guys do after one of you says that?  what's the little dance you do and teach it to me,  I wanna learn this insider's trick/step.

Am I just not ready yet? Maybe I'm not mature enough...

---

### Post by QIII on 2016-12-13
You just DID post terminal output.

---

### Post by juntjoo2 on 2016-12-13
oh... so my printer isn't printing or a program is doing something weird and this is supposed to tell someone something? what's tmpfs?  thanks

---

### Post by QIII on 2016-12-13
That was a random test.

I've seen what I need to see.  Thanks.

---

### Post by wildmanne39 on 2016-12-13
I saw your other post that was moved to wine subforum, if you are using wine I do not believe the terminal can be used to help.

---

### Post by &amp;KyT$0P# on 2016-12-13
juntjoo2, can you please post a link to this request for terminal output?  It appears that the lack of context here is causing confusion on all sides.

Thanks.

---

### Post by juntjoo2 on 2016-12-13
> **halogen2 said:**
> juntjoo2, can you please post a link to this request for terminal output?  It appears that the lack of context here is causing confusion on all sides.

Thanks.

[https://forum.winehq.org/viewtopic.php?f=2&t=28152&p=108445#p108445](https://forum.winehq.org/viewtopic.php?f=2&t=28152&p=108445#p108445)

thanks

---

### Post by &amp;KyT$0P# on 2016-12-13
That is an absurdly vague request.  Ask them what command they'd like you to run in the terminal.

---

### Post by Irihapeti on 2016-12-13
Thread closed for staff review.

---

