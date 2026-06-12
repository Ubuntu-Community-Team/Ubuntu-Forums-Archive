---
title: "HowTo: Make Actual Strong Passwords"
date: 2011-05-03
forum: Outdated Tutorials &amp; Tips
---

### Post by d3v1150m471c on 2011-05-03
Many sites and programs will suggest you use strong passwords but IMO, not many tell you properly how to go about this. IE: Things I've seen are "use a password you can remember, add special characters, etc". Naturally, some would assume from this Password!@, +=PAssword, password123, or something like this would be considered a "strong password", given that it follows the typical guides. Even on many sites, if you were to enter one of these passwords above, some flash animation would tell you it's indeed strong. I have to argue against the validity of these statements. First, I will tell you why the above type passwords are in fact weak, and secondly, how to mitigate the problem.

Now following a common theme:
```

MOnkey123
d4v1d
!!lunchmeat
h4ckth!s

```You can try these passwords in most sites and many of them will tell you they're strong. I assure you, they're not. Why?:
1.) Just because it's memorable, it should never be included in any known dictionary.
     this includes commonly used words, things personal to you, names, phone numbers,
     birthdates, etc.
2.) Changing letters around or replacing one letter with another character of a       commonly used word is ineffective.
3.) Adding characters to a commonly used word is also ineffective.
4.) These passwords are not long.

I would argue most successfully bruteforced accounts, programs, etc. are done so because one or more of the above was involved in making a password. I wrote a program specifically to show this and for security professionals and admins to mitigate bad password making. You can find it and try it out from my site below. I don't want to get into great detail about it here, but you can play around with it and discover why using a password that could even possibly show up on a dictionary(word list) is a very very bad idea, even with the common guidelines to making them "strong". 

So making a strong password. There is more than one way to do this but this is how I do it. First, we'll want to install a program called mkpasswd if it's not already installed. Next we'll want to memorize a password and a salt so we can later reproduce our new password. I would suggest using something like:
```

WubikinzzzMC72
P12B34Nj4y
VQi77i77i77

```Something that is memorable to you but definitely not going to land on an attacker's dictionary anytime soon. Additionally you'll want to make a salt value that is 8 valid characters for hash making, and make it something that is not the same as your password, but also memorable. 

So...now that we have a good password and a salt, let's hash it out:
```

mkpasswd -m md5 VQi77i77i77 W387NIDS

```And it will spit out something like this:
```

$1$W387NIDS$LO9W6I4sSn4Ua7lPBidFt/

```So...After removing the excess from that we have a solid hashed password - LO9W6I4sSn4Ua7lPBidFt . It's lengthy, definitely not in a dictionary, and you alone have to knowhow on reproducing it. Now, if you have a bad memory like mine, you could go a step further and help yourself to remember this by adding the mkpasswd output to a file, and then giving only root the ability to read and write to the file. That way, if you can at least remember the password you used, you'll still have the salt and the hash sum readily available. Additionally you can use sha-512 to make passwords with mkpasswd, but they will be lengthy and may not work with some programs or sites. Hope this keeps your stuff locked up tight :P
[COLOR=Red][B]
Additionally, for more paranoid users:[/B][/COLOR]
You may want to consider replacing a few of the hash'd characters with unorthodox characters like the copyright emblem or those not normally found on a standard keyboard layout, as a bruteforcer replicating hash sums may not consider them. Also, adding an additional string to the hash wouldn't hurt.

[COLOR=Red]**Sites with secret questions and the like:**[/COLOR]
You may consider using hash sums for secret questions regarding password recovery. Using a strong password and then having secret answers that can be easily guessed or easily **["social engineered"]("http://en.wikipedia.org/wiki/Social_engineering_%28security%29")** is asking for trouble. "Secret Questions" can be bruteforced just as easily as any other website that accepts form submission.

---

