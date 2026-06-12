---
title: "explain this unix command:"
date: 2008-08-10
forum: Programming Talk
---

### Post by sharks on 2008-08-10
ls images/*.png | sed -e ’s/\.png$//g’ >the_list

---

### Post by Alasdair on 2008-08-10
It lists all the png files in the images directory and saves them to a file called the_list minus the .png extensions. Sed is used to remove the .png extension from the end of the each filename.

---

### Post by Bachstelze on 2008-08-10
> **Alasdair said:**
> It lists all the png files in the images directory and saves them to a file called the_list minus the .png extensions. Sed is used to remove the .png extension from the end of the each filename.

.. and is a bit overkill. We have [FONT="Courier New"]basename[/FONT] for that ;)

```
for i in *.png; do basename $i .png; done > list
```

---

### Post by ghostdog74 on 2008-08-10
basename is overkill too.  Bash has internal string capabilities
```

for files in *.png
do
 echo "${files/.png/}"
done

```

---

### Post by Bachstelze on 2008-08-10
> **ghostdog74 said:**
> basename is overkill too.  Bash has internal string capabilities

Yes, but not everyone uses Bash...

---

### Post by Reiger on 2008-08-10
> **sharks said:**
> ls images/*.png | sed -e &#8217;s/\.png$//g&#8217; >the_list

Just in case, and in slightly more detail:

**[COLOR="Blue"]ls[/COLOR] images/*.png** = list all files in the folder [COLOR="#0000ff"]images[/COLOR] which contain [COLOR="#0000ff"].png[/COLOR] in their name.

**[COLOR="Blue"]|[/COLOR]** feed/pipe it to ...

**[COLOR="#0000ff"]sed[/COLOR] -e &#8217;s/\.png$//g&#8217;** ... [COLOR="#0000ff"]sed[/COLOR] and strip the [COLOR="#0000ff"].png[/COLOR] bit ([COLOR="#0000ff"]\.png[/COLOR]) located at the end ([COLOR="#0000ff"]$[/COLOR]) from each line ([COLOR="#0000ff"]/g[/COLOR]).

**[COLOR="#0000ff"]>[/COLOR] the_list** save the result as [COLOR="#0000ff"]the_list[/COLOR].

---

### Post by drubin on 2008-08-10
> **HymnToLife said:**
> Yes, but not everyone uses Bash...

Your original post was also in bash :)

---

### Post by Bachstelze on 2008-08-10
> **rubinboy said:**
> Your original post was also in bash :)

No, it works in every Bourne-like shell I've tried it in (Bash, ash, zsh and ksh). ghostdog74's, on the other hand, does not work in ash. And I remind you that Ubuntu's default /bin/sh is dash, which is based on ash, and in which it will therefore not work.


[PHP]firas@nobue ~ % cat test.sh     
#!/bin/sh                       

for files in *.png
do                
    echo "${files/.png/}"
done                     

firas@nobue ~ % ./test.sh 
./test.sh: 6: Bad substitution
firas@nobue ~ % bash test.sh 
arrow-down-double            
av_anirena_miu               
av_lily                      
av_mp_rxj
av_uf_louise                    
...
[/PHP]

In *nix jargon, it's called a bashism ;)

---

### Post by drubin on 2008-08-10
> **HymnToLife said:**
> No, it works in every Bourne-like shell I've tried it in (Bash, ash, zsh and ksh). ghostdog74's, on the other hand, does not work in ash. And I remind you that Ubuntu's default /bin/sh is dash, which is based on ash, and in which it will therefore not work.
In *nix jargon, it's called a bashism ;)
oops...

I knew there were others but I thought the default was bash and most shell scripts ran under bash.

Thanks for the correction.

---

### Post by Bachstelze on 2008-08-10
> **rubinboy said:**
> I knew there were others but I thought the default was bash and most shell scripts ran under bash.

Bash is indeed the default /bin/sh in most Linux distributions (Ubuntu is AFAIK the only one that uses another shell). However, no other UNIX or UNIX-like system that I know of uses Bash as its default shell (or even has it installed by default at all), so since the thread title said "explain this **unix** command", I went for the most universal solution, which is both easier to understand and more efficient than the sed one.

---

### Post by drubin on 2008-08-10
> **HymnToLife said:**
> Bash is indeed the default /bin/sh in most Linux distributions (Ubuntu is AFAIK the only one that uses another shell). 

Any reason why Ubuntu decided to change it? Or is it based on the fact that Debian does also.

---

### Post by Bachstelze on 2008-08-10
> **rubinboy said:**
> Any reason why Ubuntu decided to change it? Or is it based on the fact that Debian does also.

[QUOTE=man bash]
BUGS
       It&#8217;s too big and too slow.[/QUOTE]

It is also not fully POSIX-compliant.

See [http://packages.ubuntu.com/hardy/dash](http://packages.ubuntu.com/hardy/dash) to see the description of the package in Ubuntu, which explains the other reasons.

And actually, even though Dash is the Debian ash, Debian does not use or install it by default on normal systems.

[http://packages.debian.org/etch/dash](http://packages.debian.org/etch/dash)

---

### Post by mssever on 2008-08-10
> **HymnToLife said:**
> However, no other UNIX or UNIX-like system that I know of uses Bash as its default shell (or even has it installed by default at all)I know that MacOS has Bash installed by default, though the default shell (at least in 10.2) is tcsh. AFAIK, Bash is pretty much universally available on modern UNIX systems. Of course, I could be wrong. But, I never write for any shell other than Bash, and if a system doesn't include Bash, then I automatically don't care about that system.

I do think that Ubuntu using dash is a Good Thing, if for no other reason than that it teaches people that Bash isn't sh, even if you call it /bin/sh.

---

### Post by ghostdog74 on 2008-08-10
> **HymnToLife said:**
> Yes, but not everyone uses Bash...

Bash has been ported to nearly nearly every version of Unix. Since OP is posting in a Ubuntu forum, most probably he is using Ubuntu and will have Bash.

---

