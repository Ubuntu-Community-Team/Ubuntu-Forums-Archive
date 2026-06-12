---
title: "Installing perl Module"
date: 2007-04-08
forum: Programming Talk
---

### Post by cascader on 2007-04-08
**W**ould anyone like to give me advice on installing perl modules, specifically String::Tokenize but really any module installation help would be appreciated ?

There is something about this seemingly easy process of installation that I am missing.

Yes, I have done the googling, man-paging, trying to get cpan to do its thing, updated all my repositories (as one post suggested I do, didn't make any difference).

---

### Post by r00tintheb0x on 2007-04-08
Installing perl modules for what, apache?

---

### Post by r00tintheb0x on 2007-04-08
aah you mean like this

[http://search.cpan.org/dist/String-Tokenizer/lib/String/Tokenizer.pm](http://search.cpan.org/dist/String-Tokenizer/lib/String/Tokenizer.pm)

---

### Post by cascader on 2007-04-08
Thanks once again r00 (nothing to do with an Australian kangaroo ?)

Look, I guess I am pretty new to this forum thing, what I am trying to do is to install the module for getting String::Tokenizer onto my computer so that I can program in perl, building a little app for my own personal use . . . (so far). So just basically getting it installed on my system, [COLOR="Red"]**Edgy Eft**[/COLOR]. I have been to the page you suggested, and I believe that I have programmed my code properly according to the described txt, but I can't as yet test it.

I would rather tokenise a string (ordinary text, read from txt file, line at a time, put into array) without the use of a module but I am not as proficient in perl as I am in other areas . . .

thanks

---

### Post by r00tintheb0x on 2007-04-08
Im no programmer but check this out [http://www.monodevelop.com/Main_Page](http://www.monodevelop.com/Main_Page)

---

### Post by cascader on 2007-04-08
Yes, I am very interested in the mono project. What, have you got any ideas ? I like the way that they are getting closer to invading the Windows hemisphere by .net compatibility. I have all the modules and the IDE installed so once my perl project is out of the way it might be time for a cup of mono.

 Very OT, I know, better get back to trying to dig up module install info. Thanks r00 . . .

---

### Post by cascader on 2007-04-08
Alright,  what I didn't do was search these posts first. So hopefully a lesson learnt.

Am following post [here]("http://ubuntuforums.org/showthread.php?t=158268&highlight=module+perl"), currently running [COLOR="Red"]**sudo perl -MCPAN -e shell**[/COLOR] as suggested.
Thanks

---

### Post by tr333 on 2007-04-09
you should be able to just run "sudo cpan" to start the cpan shell.
after the config has been setup for the first time, type "install String::Tokenizer" at the cpan shell prompt.
type "exit" to quit from the cpan shell.

---

### Post by cascader on 2007-04-09
Alright, thanks **[COLOR=Red]tr333[/COLOR]**, just as I was researching this next step. Am appreciating the benefits of forum cruising as a source of shared problems . . . I'm not alone, ;-)

---

### Post by cascader on 2007-04-28
Just posting an update, in case anyone here has a similar problem . . .

My initial problem was that I could not seem to tokenize white space delimited strings. 

Sounds easy, doesn't it. I have had a bit of experience writing perl scripts, but for some reason have not come across this problem. Well, I have finally abandoned the idea of using a module and fallen back on a simple regex . . . der, I know, but we all have to find out these things the hard way . . .

Anyways, for posterity . . .
[B]        [COLOR=YellowGreen]# Line Tokeniser reaped from:
        # Doran Barton pluglist at plug.org
        # Wed Nov 3 13:00:38 MST 2004[/COLOR]
    [COLOR=Red]$line[/COLOR] =~ [COLOR=Teal]s/\\ /\t/g[/COLOR];
    [COLOR=Red]@tokens[/COLOR] = [COLOR=Purple]split[/COLOR] [COLOR=Teal]/ /[/COLOR], [COLOR=Red]$line[/COLOR];
[/B]

---

