---
title: "command line password generator"
date: 2015-10-06
forum: New to Ubuntu
---

### Post by eeeark1 on 2015-10-06
I'm looking for some guidance in regard to terminal commands. I found this little thing in a reddit post while searching for something about diceware. 
```
cat /usr/share/dict/words | sort -R | head -n 10
```
It spits out ten random words from the dictionary that comes with any ubuntu install, as far as I can tell.

This is the link if anyone's interested: [https://www.reddit.com/r/AskNetsec/comments/15cra4/alternative_diceware_word_list/](https://www.reddit.com/r/AskNetsec/comments/15cra4/alternative_diceware_word_list/)

I am wondering how one would go about making this a little more useful. How could I make it output only words that don't have an apostrophe or words that are shorter than 10 letters ( or 11, 12, etc.). Any other ideas would also be helpful. I'd like to make it give good passphrases that are more easily memorized. Of course, it's useful as is. I can just take words I deem appropriate or just take the root of the words it outputs if they're too long. It seems fun to mess with it more though. 

Any input on security would also be nice. Comparing this to diceware, on the surface it seems like it could be better but I'm definitely not a security expert. It seems like there are more words in the ubuntu dictionary (diceware~7,700 ubuntu~99,000 according to some of the posts in the link above) but when we start filtering them like this I wonder how many we're taking out. Are there any problems with the "randomness" of *sort -R*? Any other issues with this method that I'm not aware of?

Thanks in advance, and if I've posted this in an inappropriate place, I apologize..

I don't actually use this btw. It's more to just help me learn the cmd line a little better.

---

### Post by Frogs Hair on 2015-10-06
You might want view this also.  
[http://www.howtogeek.com/howto/30184/10-ways-to-generate-a-random-password-from-the-command-line/](http://www.howtogeek.com/howto/30184/10-ways-to-generate-a-random-password-from-the-command-line/)

---

### Post by eeeark1 on 2015-10-06
That's a cool page, thanks. The thing I like about the one I posted is that it will give a passphrase (of sorts) as opposed to just a password. Seems like a passphrase could be a little more secure. Also, I use lastpass and am not exactly sure about the security of this, so I'm not planning on really using it. I would just like to learn how to filter out some of the unusable words it outputs.

---

### Post by Habitual on 2015-10-07
```
#!/bin/bash
date +%s | sha256sum | base64 | head -c 12 ; echo
date +%s | sha1sum | base64 | head -c 12 ; echo
< /dev/urandom tr -dc _A-Z-a-z-0-9 | head -c${1:-12};echo;
```

or use pwgen from repo like so:
```
pwgen 12 -ys1
```

Pass phrase?
"Scooter my daisy head" as a password?

See also [http://code.activestate.com/recipes/410076-generate-a-human-readable-random-password-nicepass/](http://code.activestate.com/recipes/410076-generate-a-human-readable-random-password-nicepass/)

---

### Post by Lars Noodén on 2015-10-07
> **eeeark1 said:**
> I am wondering how one would go about making this a little more useful. How could I make it output only words that don't have an apostrophe or words that are shorter than 10 letters ( or 11, 12, etc.).


The tool [grep](http://manpages.ubuntu.com/manpages/trusty/en/man1/grep.1.html) can help with that.  

```

grep -E "^.{11,}$" /usr/share/dict/words | grep -v "'" | sort -R | head -n 10

```

That will get words only 11 letters or longer, but without apostrophes.

As far as the randomness of sort goes, that depends on which algorithm it uses.  [sort](http://manpages.ubuntu.com/manpages/trusty/en/man1/sort.1.html) is in the package coreutils.  So you can grab the source like this:

```

cd /tmp
apt-get source coreutils

```

---

### Post by mcduck on 2015-10-07
I'd recommend just using APG, which is available in Ubuntu's repositories. Take a look at this page for instructions: [https://help.ubuntu.com/community/StrongPasswords]("https://help.ubuntu.com/community/StrongPasswords")

---

### Post by eeeark1 on 2015-10-07
Thanks for your help, folks. I'm not really looking to make  passwords/phrases with this, though. Not ones I'd actually use anyhow. I  just saw this thing and played around with it a little. I was simply  trying to learn more about using the terminal effectively. Perhaps the tags I put in made this confusing, sorry.
[B]
Lars[/B]: Thanks, this is what I'm talking about. I'm not sure how I forgot about *grep, *duh. 
```
*grep -E "^.{11,}$" /usr/share/dict/words | grep -v "'" | sort -R | head -n 10*
```
I think I understand most of what your doing there but (after -E) would it be possible the explain the *"^.{11,}$" *part? I get that this is where you're saying get words 11 letters or longer, but I don't understand the period or dollar sign parts.

---

### Post by HermanAB on 2015-10-07
It has been done to death already:
pwgen, genpass, makepasswd, passwordmaker...

I prefer using keepassx, to store and manage passwords and it also has a password generator built in.

---

### Post by Lars Noodén on 2015-10-08
The -E in grep means use an [extended regular expression](http://www.regular-expressions.info/posix.html).  The caret ^ means match the beginning of the line.  The dollar sign means macth the end of the line.  The dot means any character.  {11,} means match 11 or more of the preceding, which in the above case is a dot which means match 11 or more of any characters.  Having that between ^ and $ means match any 11 that go from the start of the line to the end of the line.  If you want five or less, then {,5} matches that.  If you want words between five and nine letters long, then use {5,9} and so on.  

In GNU grep, which is what Ubuntu runs, you also have the option -P to do [Perl regular expressions](https://www.cs.tut.fi/~jkorpela/perl/regexp.html) which can get [quite complex](http://perldoc.perl.org/perlre.html).

Have fun.

---

### Post by Topsiho on 2015-10-08
Edit: Python script removed as indents in front of lines are removed, making script unusable.
Sorry for this

Topsiho

---

