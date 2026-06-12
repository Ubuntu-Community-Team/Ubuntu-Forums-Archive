---
title: "how did you learn vim?"
date: 2010-05-29
forum: Programming Talk
---

### Post by l3ecl on 2010-05-29
I'm interested in becoming proficient using vim. How did you do it? Please share your experiences, especially any tutorials/exercises you used to master vim.

---

### Post by ad_267 on 2010-05-29
By opening a terminal and running "vimtutor". Work through all of that and then just keep using vim for everything. If you think there should be an easy way to do something in vim, google it and you'll probably find it. You'll probably be constantly learning new things about vim, but once you know the basics you should already be a lot faster than with other editors.

That's pretty much how it worked for me anyways :)

---

### Post by abhilashm86 on 2010-05-29
get yourself a vim book or online reference..........
best way to play with vim is keep editing aliases, edit all system and text files only with vim, use more navigations like k,l,j. 
without vim, you can use vim by using 
```
 
vim.tiny

```

By within no time you'll be master in vim:P

---

### Post by shawnhcorey on 2010-05-29
First, I use ex.  Then when vi came out, I switched to it.  And when vim came out, I switched though I prefer gvim.  I haven't learned much vim; the vi commands cover 99% of my work.

The [official ViM site]("http://www.vim.org/").

---

### Post by ryry46d9 on 2010-05-29
[http://www.fprintf.net/vimCheatSheet.html]("http://www.fprintf.net/vimCheatSheet.html") has been my friend

---

### Post by juancarlospaco on 2010-05-29
I use ed

---

### Post by trent.josephsen on 2010-05-29
> **l3ecl said:**
> I'm interested in becoming proficient using vim. How did you do it? Please share your experiences, especially any tutorials/exercises you used to master vim.

The real clincher for me was the regex support.  With some Perl under my belt, I suddenly realized that I could use regular expressions to search files and :s// to do sophisticated substitutions all in the comfort of my editor.  So after vimtutor, I'd suggest learning regular expressions and how to use them in Vim.

---

### Post by km0r3 on 2010-05-29
The way I learned Vim was vimtutor. It really covers all to get you started. Maybe after a week of practicing I was already moderately fast in editing multiple system files and coding.

Oh, the cheatsheet linked to earlier is also a great for recalling things in the future.

---

### Post by timvoet on 2010-05-29
you can also take a look at vimcasts ( [http://vimcasts.org/](http://vimcasts.org/) ) it's an ongoing video podcast series that explains different things you might be tring to do.  it also shows comparisons, i.e. if my normal editor i do this, in vim i can do this.

---

### Post by l3ecl on 2010-05-30
thanks for the vim tutor heads up! and also the vim cheat sheet, ive added it in my bookmark.

what other applications do you guys use vim for?

---

### Post by lisati on 2010-05-30
<off topic>
Apparently, Vim can be used together with elbow grease to work wonders.

And for the benefit of NZ forum users of my generation: yes, I went to school in Pakuranga.
</off topic>

---

### Post by BoneKracker on 2010-05-30
> **l3ecl said:**
> I'm interested in becoming proficient using vim. How did you do it?

Like this:
](*,)



[COLOR="White"].[/COLOR]

---

### Post by xsinsx on 2010-05-30
Run the tutorial and use it everyday as much as possible. thats how i did it.

---

### Post by bunburya on 2010-05-30
Can someone tell me what are the main advantages of using vim over simpler editors like nano or GUI-based editors like gedit? I'm a noob when it comes to programming, is vim really only helpful for more complex coding projects are does it benefit simpler tasks as well?

---

### Post by xsinsx on 2010-05-30
VIM is an all purpose text editor. The big thing when learning it is that you never have to leave the terminal while using it that was a big plus for me. another thing is when in command mode in VIM you can still execute some shell commands like this !:ls and of course that is handy if you need to gather information about the directory you in while you scripting. when learning it there are a few things that just makes fixing and moving around the text file much much faster like using the w, or e.

---

### Post by SoFl W on 2010-05-30
Once I remembered the basic commands the rest came easy.  [THIS]("http://www.tuxfiles.org/linuxhelp/vimcheat.html") page helped out a lot.

> **bunburya said:**
> Can someone tell me what are the main advantages of using vim over simpler editors like nano or GUI-based editors like gedit? I'm a noob when it comes to programming, is vim really only helpful for more complex coding projects are does it benefit simpler tasks as well?

I do/did a lot of SSH connections where I didn't have a GUI, just a command line so learning something that is on most systems was useful.  My boss (at the time) preferred 'nano' and on systems he compiled he didn't include vim, but vi or vim is on most every system I have worked on.

---

### Post by filosophem on 2010-05-30
As BoneKracker said: by struggling for 3 weeks ](*,)

btw, add this "set showcmd" (without the quotes) to your .vimrc and you'll always know in which mode you are


happy vimming !!!

---

### Post by xsinsx on 2010-05-30
> **filosophem said:**
> As BoneKracker said: by struggling for 3 weeks ](*,)

btw, add this "set showcmd" (without the quotes) to your .vimrc and you'll always know in which mode you are


happy vimming !!!

That is an amazing idea thank you. I had never thought of doing that. even though im not the OP i learned something right there.

---

### Post by MCVenom on 2010-05-30
Well, I used to not understand why anyone used vi/vim/emacs when we had nano to make everything easier (this was a month or two ago, and I still don't get why people use emacs! :lolflag:). Then I Googled 'Why do people use vi' and found this: [B][Why, oh WHY, do those #?@! nutheads use vi?]("http://www.viemu.com/a-why-vi-vim.html")

[/B]I skimmed through that and found a link to this at the bottom; it hit home more for me because I was using a laptop. :P: [**The Vi Input Model**]("http://blog.ngedit.com/2005/06/03/the-vi-input-model/")

So I finally gave into my curiosity, opened up a terminal and tried it with vimtutor. I learned the basics quickly; I also had the feeling that its difficulty is overexaggerated. It wasn't nearly as hard to get used to as people made it out to be, IMO. But that's just me. :P

Personally, I just did it because I thought it'd be a fun way to kill a half hour; but it has it's uses. I hear most *nix systems come with vi/vim by default, so that's definitely one advantage; the other is one I can vouch for by experience, you may someday encounter a system that doesn't have conventional meta/modifier keys (nano and emacs require them and by these I mean Ctrl, Alt, Shift, etc.). I was setting up a basic CLI Ubuntu environment on a Motorola Droid; Vi/Vim are almost the only usable cli editors on that device, because it's modifier keys don't really correspond to anything the other editors are programmed to make use of.

Overall, learning Vim is a worthwhile experience, and one I'd definitely recommend. :D

---

### Post by hockey97 on 2010-05-30
Sorry to intrude but what is vim?

I would like to know since I don't know and never heard of it.

---

### Post by shawnhcorey on 2010-05-30
> **hockey97 said:**
> Sorry to intrude but what is vim?

I would like to know since I don't know and never heard of it.

ViM is a text editor.  Here is it's [official website]("http://www.vim.org/").

ViM is based on a very old line editor, ed(1).  ed(1) allows to to edit one line at a time.  ed(1) was extended with a whole bunch of commands and became ex(1) (Ed eXtended).  After a while, terminal movements commands were added, creating a multi-line editor, vi(i) (VIsual editor).  Later, even more improvements where added, creating ViM (Vi IMproved).  A GUI interface was added to it, creating gvim (GUI-ViM).

As a side note, Microsoft took ed(1), removed some of its commands and created edlin.  You might have hear of it.

If you're running Ubuntu, et al., the package to download is called gnome-vim.

---

