---
title: "total perl n00b needs help for thunderbird -&gt; vcard script"
date: 2005-05-08
forum: Programming Talk
---

### Post by 23meg on 2005-05-08
first off, i'm not entirely sure if i'm not abusing the programming section with a drive-by practical help request; forgive my lameness if this is the case, but this seemed too perl-related to be in the "other applications" section..

what i want to do is transfer my thunderbird contacts to my ipod mini. the mini accepts contacts in vcard format, and i know that thunderbird doesn't have built in support for exporting vcard files from its adress book. [some folks are developing an extension](http://vcard.mozdev.org/) that will allow this, but it's in the works yet. however, i've found [this perl script](http://hacks.traveljury.com/) that claims to do exactly what i want. trouble is, i'm a total alien to perl, and don't know how to make use of the script. i've made it executable by applying chmod +x to it, but that's how far i've got. ,

the part i'm stuck with is how to get the actual output from the script. it says in the comments that

> 	vCards are printed to STDOUT, so can be redirected in the usual way:

	  $progname > vcards_file_name
	  $progname | recode UTF8..ISO-8859-15 > vcards_file_name 

now, what i want to learn is how to actually redirect STDOUT to a vcard file. any help is appreciated.

---

### Post by LordHunter317 on 2005-05-08
Do just what the script says.

Run it on the command line, and give it '>' and the filename ytou want to save the vcard as as the last two parts of the line.

So if it's called 'vcard.pl', you'd do:```
vcard.pl [arguments] > myvcard.vcard
```and you'd have the output in myvcard.vcard.

---

### Post by 23meg on 2005-05-08
i've tried that, but i get a "mab2vcard.pl: command not found" error on the console, and an empty vcard file (0 bytes).

---

### Post by LordHunter317 on 2005-05-08
[QUOTE=23meg]i've tried that, but i get a "mab2vcard.pl: command not found" error on the console, and an empty vcard file (0 bytes).[/QUOTE]It's not in your PATH then.  The eaisest way is to cd to the directory the script is in and prepend ./ to it's name.

---

### Post by 23meg on 2005-05-08
i've checked that too; i'm sure it's in my path.

here's how i've got it working (trial and error..):

```
perl mab2vcard [path including filename] > [vcard filename] 
```

no matter what i've tried, i couldn't get the script to recognize the path i entered in the line

```
use constant ABOOK_PATHS => qw ( **path** );
```

tried entering the exact path of the adress book file, including and excluding filename, no luck. so i specified it as a command line paramater, and voila, it works.

for reference: the script doesn't do its job very well though; deleted contacts are still transferred to the vcard file (this is listed as a bug), and any non-western charactes are messed up once on the ipod, even though the script seems to be using utf8. i could still use a hand with the latter issue.

thanks for your attention..

---

