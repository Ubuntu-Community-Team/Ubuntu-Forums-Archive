---
title: "Simplifying the find command"
date: 2013-03-10
forum: New to Ubuntu
---

### Post by GrouchyGaijin on 2013-03-10
Hi Folks,

I recently learned how to use:

```
find / -name *Whatever I'm looking for* -print 2> /dev/null


```
to find things on my system.

My question is, is there a way to set this as a bash alias that will allow me to put whatever I want to search for between the *s before running the command? 

Ideally I'd type the alias in the terminal and then be able to edit the command before it launches.  It seems that when whenever I use an alias, the command is executed right then.

---

### Post by ViliX64 on 2013-03-10
I think they are not, this is just final form of the command, it just needs those argument. But maybe, you can create shortcut for running terminal in /dev/null/ and then you could not write it there..

---

### Post by MG&amp;TL on 2013-03-10
In most cases *locate* is faster than *find* for this sort of thing:

```
locate "whatever you're looking for"
```

NB: *locate* uses a database of files (update periodically) to speed up access, so if you've just added some new files and you need to look for something, you probably want to update that database:

```
sudo updatedb
```


As for your actual question, I'd use a bash function: [http://tldp.org/LDP/abs/html/functions.html](http://tldp.org/LDP/abs/html/functions.html)

E.g if you put this in your .bashrc file:

```

function greet {
    echo "Hello, $1"
}

```

You could then do this:

```
$ greet michael
Hello, michael
$
```

I'm sure you can see how you could adapt this. :)

---

### Post by prodigy_ on 2013-03-10
```
read -p "Searching for: " search_string; find / -name "$search_string" 2>/dev/null
```

---

### Post by sudodus on 2013-03-10
I suggest that you keep the freedom of choice and use the wild card character * in your search pattern. If you add sudo, you will be allowed to search also directories where the normal user has no access. So I suggest the following two aliases, ***localfind*** to search the current directory and its subdirectories, and ***rootfind*** searching the whole computer.

```
alias localfind='sudo find \. -name'
alias rootfind='sudo find / -name'
```
Enter these (or something similar) into your [FONT=courier new]**.bashrc**[/FONT] file at the alias commands that are already there!

So if you don't want to wait for rootfind, it can be a good idea to change directory to a relevant directory and run localfind.

examples:

```
cd
localfind "*bash*"

```
```
cd /etc
localfind "*host*"
localfind "*grub*"

```
```
rootfind "*grub*"
```
*Edit:* another example shows the advantage with flexible usage of *
Compare the output of these commands:
```
cd /usr
localfind "*.doc*"
# and
localfind "*.doc"
```

Good luck :-)

---

### Post by GrouchyGaijin on 2013-03-10
Thank you for all of the answers guys, I really appreciate it.

I have follow up questions so I'll go in order that you replied.

[COLOR=#0000cd]@MG&TL: When I try locate, even after updating the database, I am unable to find files that I know exist.  For example, a song I have stored on the internal hard drive and on an external hard drive.  Using the command I posted however, finds both copies of that song.

I'm afraid I don't understand how a function works (I'll check the link you posted.), basically what I want to do is be able to type a short command followed by the string I am looking for.  In your example:

```
function greet {    echo "Hello, $1"
}
```
where is the search string?[/COLOR]

[COLOR=#ff0000]@Prodigy_

Your suggestion looks like something I was imagining.  Where exactly would I put your code?
```
read -p "Searching for: " search_string; find / -name "$search_string" 2>/dev/null
```
and how would I call it?[/COLOR][COLOR=#00ff00]
[/COLOR]
[COLOR=#006600]@sudodus

I tried putting ```
alias rootfind='sudo find / -name'
```
in my list of bash_aliases and then running:
```
rootfind part-of-the-name-of-file
```
The search returned no results.[/COLOR][COLOR=#006633]
[/COLOR]
However if I run ```
find / -name *part-of-the-name-of-the-file* -print 2> /dev/null
```
I get a list of, using the example of searching for a specific song, two hits, both versions of the song I'm looking for.  One on the internal hard drive and one on the external drive.

So basically, the code I have works and does what I want.  I'm just looking for a way to be able to type something shorter in the terminal.

---

### Post by sudodus on 2013-03-10
> **GrouchyGaijin said:**
> [COLOR=#006600]
```
rootfind part-of-the-name-of-file
```
The search returned no results.[/COLOR][COLOR=#006633]
[/COLOR]
You need the wild card characters! I explained why I suggest you use them, and showed with examples

[COLOR=#006600]```
rootfind "*part-of-the-name-of-file*"
```[/COLOR]

It is also good to enclose in double-quotes ("), otherwise there will be problems when instances are found in the current directory. Try the examples that I supplied. If they don't work for you, I will try hard to improve them.

I think Prodigy_'s suggestion is fine. Make an alias of it!

---

### Post by GrouchyGaijin on 2013-03-10
Prodigy_'s solution works well.

Thanks guys!

---

### Post by MG&amp;TL on 2013-03-10
> **GrouchyGaijin said:**
> Thank you for all of the answers guys, I really appreciate it.

I have follow up questions so I'll go in order that you replied.

[COLOR=#0000cd]@MG&TL: When I try locate, even after updating the database, I am unable to find files that I know exist.  For example, a song I have stored on the internal hard drive and on an external hard drive.  Using the command I posted however, finds both copies of that song.

I'm afraid I don't understand how a function works (I'll check the link you posted.), basically what I want to do is be able to type a short command followed by the string I am looking for.  In your example:

```
function greet {    echo "Hello, $1"
}
```
where is the search string?[/COLOR]


Hm. That's weird, maybe locate stays on the same disk if it can.

Functions allow you to substitute arbitrary commands into sub-commands. Sorry, I should have been a little bit clearer, the example I posted was just an example. You probably want something like (in bashrc):

```

function search {
    find / -name $1 -print 2> /dev/null
}

```

Then you could do:

```

search "Whatever you're looking for"

```

---

### Post by sudodus on 2013-03-10
> **GrouchyGaijin said:**
> ...
As for "[COLOR=#000000]I think Prodigy_'s suggestion is fine. Make an alias of it!"
Bear with me, how exactly do I make an alias of this?:
[/COLOR]

```
alias myfind='read -p "Searching for: " search_string; find / -name "$search_string" 2>/dev/null'
```

You can run this in your terminal window and get a temporary alias. Run it with ```
myfind
```
and if you want it permanent, enter it into your **[FONT=courier new].bashrc[/FONT]** (or .bash_aliases file).

The following alias is a modified version of [COLOR=#000000]Prodigy_'s suggestion, which includes the wild cards according to the OP. Choose the one that is better for ***you***[/COLOR]
```
alias myfind='read -p "Searching for: " search_string; find / -name "*$search_string*" 2>/dev/null'
```

Good luck :-)

---

### Post by schragge on 2013-03-25
Slightly modified version of **prodigy_**'s alias to work with a command line parameter like a shell function (but using real shell function is much better):
```
alias myfind='sh -c "find / -name \"*\$**\" 2>/dev/null" _'
```

---

