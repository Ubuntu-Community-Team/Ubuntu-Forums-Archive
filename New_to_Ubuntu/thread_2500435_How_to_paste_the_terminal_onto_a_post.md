---
title: "How to paste the terminal onto a post ?"
date: 2024-09-01
forum: New to Ubuntu
---

### Post by Innernet on 2024-09-01
Hi.  

There is a much preferred 'proper' way the terminal should be pasted onto a post instead of just highlighting, copying and pasting its text.
I believe allows someone responding a thread to act on the shown terminal results... or something like that.

Can someone please detail all the keystroke steps sequence to do it right ?  It is not supposed to be a 'screenshot' either if I remember well ?

---

### Post by Rubi1200 on 2024-09-01
The best way to share terminal output on the forum is like this:

1. highlight and then copy the output
2. when replying or starting a new post click on Go Advanced at the bottom of the editor
3. paste the output and then highlight
4. click on the # icon in the editor tools

Doing this will wrap the text with code tags. This makes it much easier to read and analyze for everyone.

Ideally, you should also use code tags to highlight commands you are using.

For example,

```
cat etc/default/grub
```

Sample output:
```
GRUB_DEFAULT=0
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""

```

Hope this helps.

---

### Post by oldfred on 2024-09-01
Copy & paste with code tags.
Easy to add in Forum's Go Advanced editor with highlight & then # icon.
[https://ubuntuforums.org/showthread.php?p=12776168#post12776168](https://ubuntuforums.org/showthread.php?p=12776168#post12776168)

I often am in quick reply and use quote tags, and edit quote to code.
or just type 
If using Quick Reply then[noparse] ```
 at the beginning and 
``` at the end. [/noparse]

```
[FONT=monospace][COLOR=#54ff54]**fred@z170-noble**[/COLOR][COLOR=#000000]:[/COLOR][COLOR=#5454ff]**~**[/COLOR][COLOR=#000000]$ ll *.txt [/COLOR]
-rw-rw-r-- 1 fred fred 11621 Aug 12 13:43 backup2024_deleted.txt

[/FONT]
```

Sometimes I use mouse & right click & sometimes terminal, but paste in terminal is control, shift v where in gui its just control v.

---

### Post by Innernet on 2024-09-01
Thanks, seems I will be able to remember plus will make a note for reference on the desktop.
What are the 2 icons left and right of the arrowtip ?  Are for 2 different 'code' things ?  They express the same when hovering on.

---

### Post by oldfred on 2024-09-01
Left icon says "quote" which is same as in quick reply.

---

### Post by deadflowr on 2024-09-02
Arrowtip?
You mean the special code tags for html and php outputs?

In order the left icon that looks like a word bubble is the quote tag.

The second that looks like a hash tag is the code tag, which is the standard tag we prefer to use for any terminal output.

The third that looks like bi-directional arrows is the html code tag which is used when posting any html code.
It keeps the html formatting in place, so it'll show the correct colors and whatnots.

The last that looks kind of like a document file, is the php code tag.
It keeps the proper formatting in place for any php code output that is posted.
Much like the html does but for php code.

That help?

---

### Post by Innernet on 2024-09-02
Thank you, deadflowr.  
Yes, the word bubble and the #.  Yes, helps as you always do.

---

