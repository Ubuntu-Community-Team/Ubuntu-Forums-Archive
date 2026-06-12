---
title: "Using Vim like notepad"
date: 2008-12-01
forum: Programming Talk
---

### Post by john_spiral on 2008-12-01
Hi,

Before you fry me for using the words Vim and notepad in the same line, let me explain ;-)

Is there an option in Vim to highlight a portion of text then use that portion of text in a find and replace across the whole file?

Much like highlighting some characters/words in notepad, pressing CTRL + C (to copy) then CTRL + H (to open the find/replace window) then CTRL + V (to paste the highlighted text in the "Find what" field), then completing the "Replace with" field, before clicking "Replace all".

From my Googling I've come across pressing ‘:’ while in visual mode to run a search on the highlighted section - not what I'm looking for.

How about using the highlighted section in the search itself?

thanks

John

---

### Post by __Ryan__ on 2008-12-01
you can use a sed command inside the command mode:

for example:

```
:%s/**old\ statement**/**new\ statement**/g
```

this will replace "old statement" with "new statement", notice that you have to use the backslash character to escape the space " " characters. Also the 'g' at the end will search and replace all instances in the file.

Remember you also have to be in command mode by hitting escape before you try this. 

Have fun, this is a very powerful tool once you learn how to use it correctly.

---

### Post by sujoy on 2008-12-01
add some regex skills with the above and you have the most powerfull search/replace ever made

---

### Post by john_spiral on 2008-12-01
Thanks for the replies so far.

Forgot to mention that the file I was looking to run a find / replace on, has some hidden TABS & spaces (Windows file).

Ryan your **sed** approach does look good but I would prefer to run the find / replace within Vim. This will give me a visual sense of what I'm running it against and I won't need to know how to format TAB character's in a **sed** command.

I'm keen on using Vim over notepad for reasons of speed & accuracy.

I'll do some more Googling.....

thanks

John

---

### Post by john_spiral on 2008-12-01
looks like I found what I was looking for:

[http://www.vim.org/scripts/script.php?script_id=848](http://www.vim.org/scripts/script.php?script_id=848)

Is there no easy way to do this?

---

### Post by __Ryan__ on 2008-12-01
What your looking for doesn't exist, at least with vim. You need to escape certain characters such as spaces even with find. What you can do is run a find to see what it highlights, and then drop that search in a sed command.

It is much easier to learn the best way to do things in VIM than try to alter its functionality to suit your past experiences with other text editors. The power of vim comes from is differences not its similarities. It has a very a steep learning curve to be sure, but benefits you will see are well worth it in my opinion.

just my 2 cents :)

Good luck

---

### Post by stylishpants on 2008-12-01
1. Select your text, and yank it.  (press y to yank )

2. Enter command mode and start the substitution operator (type :s/ )

3. Paste into the command mode prompt: (type Ctrl-r")

4. Since the s/// operator won't work for multi-line searches, look at what you pasted and remove any trailing ^M characters that might have gotten pasted in.

5. Finish your substitution operator (type the next //, with a replacement string between them if desired)

6. Hit enter to submit the command

---

### Post by john_spiral on 2008-12-02
Thanks for the reply stylishpants!

I'll have a closer look this eve.

---

### Post by Greyed on 2008-12-03
> **john_spiral said:**
> Ryan your **sed** approach does look good but I would prefer to run the find / replace within Vim.

That **is** from within vim.  

[http://www.geocities.com/volontir/#substitute](http://www.geocities.com/volontir/#substitute)

Why he called it a "sed" command is beyond me.  He is also wrong about having to escape spaces.

---

### Post by forrest charnock on 2009-10-27
> **john_spiral said:**
> Thanks for the replies so far.

Forgot to mention that the file I was looking to run a find / replace on, has some hidden TABS & spaces (Windows file).

Ryan your **sed** approach does look good but I would prefer to run the find / replace within Vim. This will give me a visual sense of what I'm running it against and I won't need to know how to format TAB character's in a **sed** command.

I'm keen on using Vim over notepad for reasons of speed & accuracy.

I'll do some more Googling.....

thanks

John

I have no idea how well it would work but notepad comes bundled with wine. I was going to see if it would let me open jpg's like it does in windows but no cigar. Of course someone with the skill could maybe tweak wine and make it work.

---

### Post by petrus4 on 2009-10-27
John,
I'd recommend checking out vis.  Try 'man vis.'  I don't know whether it is installed on Ubuntu or not by default, but it is on FreeBSD.

Vis is a command line filter program specifically for displaying invisible chars in files, in a visible way.

```

vis -lt <file>

```

The above command will print a file to stdout, and will insert special chars for both tabs and newlines, to show you where they are in the file.

---

### Post by TheStatsMan on 2009-10-28
Gvim has exactly what you are asking for. You can simply highlight goto edit -> find and replace

---

