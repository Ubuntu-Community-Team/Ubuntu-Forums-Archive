---
title: "[SOLVED] BASH script to rename files that contain '.07.09.16' to '-20070916'"
date: 2007-09-16
forum: Programming Talk
---

### Post by altonbr on 2007-09-16
I'm looking to write a BASH script (tested heavily of course) to rename all of my files that contain dates in semi-ISO standards to ISO standards.

As the name claims, I currently date files with: "*.07.09.16*", but would like to rewrite them to "*-20070916*".

The tricky part is that the date is not always at the end of the filename. Since it's essentially meta-data, I enter it in which ever place I feel it should be sorted in.

**ie:** <most_important>.<second_importance>.<third_importance>.<file_extension>
**real example:** pidgin-interface_proposal.07.09.16.xcf
**change to:** pidgin-interface_proposal-20070916.xcf

Problem is, I have thousands upon thousands of files like this (essentially every file on my hard drive) in this format so I (1) Don't have time to re-write every file (2) Need the script to work perfectly.

Now of course I'll backup ALL my data before running this, but I figure to be safe, the script should only run in the current directory and it's children.

Also, I have zero (or close to none) files that appear before 2000.

What would be the best method? I quick BASH script? Python?

Thanks for your time! :)

---

### Post by gautada on 2007-09-16
It is not hard to write a bash script and you will learn so much, try:

[LIST]
[*][BASH]("http://www.hypexr.org/bash_tutorial.php")
[*][SED]("http://www.grymoire.com/Unix/Sed.html")
[*][AWK]("http://www.vectorsite.net/tsawk.html")
[/LIST]

---

### Post by bashologist on 2007-09-16
test:
```
foo@bar:~$ touch 'pidgin-interface_proposal.07.09.16.xcf'
foo@bar:~$ rename -n 's/\.(\d{2})\.(\d{2})\.(\d{2})/-20$1$2$3/' 'pidgin-interface_proposal.07.09.16.xcf'
pidgin-interface_proposal.07.09.16.xcf renamed as pidgin-interface_proposal-20070916.xcf
foo@bar:~$
```

code:
```
rename 's/\.(\d{2})\.(\d{2})\.(\d{2})/-20$1$2$3/' *
```Make sure to test it first. Make backups.

---

### Post by altonbr on 2007-09-16
> **bashologist said:**
> test:
```
foo@bar:~$ touch 'pidgin-interface_proposal.07.09.16.xcf'
foo@bar:~$ rename -n 's/\.(\d{2})\.(\d{2})\.(\d{2})/-20$1$2$3/' 'pidgin-interface_proposal.07.09.16.xcf'
pidgin-interface_proposal.07.09.16.xcf renamed as pidgin-interface_proposal-20070916.xcf
foo@bar:~$
```

code:
```
rename 's/\.(\d{2})\.(\d{2})\.(\d{2})/-20$1$2$3/' *
```Make sure to test it first. Make backups.

Wow, that's fantastic. I never knew there was a binary for this! Good ol Linux an d it's command line tools.

So here's my test:

```
brett@dell-xps-gen5:~$ mkdir test
brett@dell-xps-gen5:~$ cd test/
brett@dell-xps-gen5:~/test$ touch 'pidgin-interface_proposal.07.09.16.xcf'
brett@dell-xps-gen5:~/test$ touch 'pidgin-.07.09.16-interface_proposal.xcf'
brett@dell-xps-gen5:~/test$ touch '07.09.16-interface_proposal-02.xcf'
brett@dell-xps-gen5:~/test$ man rename
brett@dell-xps-gen5:~/test$ rename 's/\.(\d{2})\.(\d{2})\.(\d{2})/-20$1$2$3/' *
brett@dell-xps-gen5:~/test$ ls
07.09.16-interface_proposal-02.xcf
pidgin-interface_proposal-20070916.xcf
pidgin--20070916-interface_proposal.xcf
```

I did those extra touches to mimic the other styles and variations of dates I have in files. So I guess it should look for anything that has xx.xx.xx with only the periods in between and nothing else... if it has a leading period, replace it with a dash, if not, or if it has a leading dash, do nothing.

Also, how can this work recursive? The manual says it only has three flags:

>        -v, --verbose
               Verbose: print names of files successfully renamed.

       -n, --no-act
               No Action: show what files would have been renamed.

       -f, --force
               Force: overwrite existing files.

So the code would now look like this, without worrying about recursion or that if statement:

```
rename 's/(\d{2})\.(\d{2})\.(\d{2})/20$1$2$3/' *
```

I just need to figure out that "if there is a leading dot, turn it into a -" because ls returned this:

> 20070916-interface_proposal-02.xcf
pidgin-interface_proposal.20070916.xcf
pidgin-.20070916-interface_proposal.xcf


Thanks for your help thus far; I'm learning!

---

### Post by bashologist on 2007-09-16
test:
```
test[0]='pidgin-interface_proposal.07.09.16.xcf'
test[1]='pidgin-.07.09.16-interface_proposal.xcf'
test[2]='07.09.16-interface_proposal-02.xcf'
touch "${test[@]}"
rename -n 's/[\.-]*(\d{2})\.(\d{2})\.(\d{2})/-20$1$2$3/; s/^-//' "${test[@]}"
```

output:
```
pidgin-interface_proposal.07.09.16.xcf renamed as pidgin-interface_proposal-20070916.xcf
pidgin-.07.09.16-interface_proposal.xcf renamed as pidgin-20070916-interface_proposal.xcf
07.09.16-interface_proposal-02.xcf renamed as 20070916-interface_proposal-02.xcf
```

recursion:
```
find -type f -exec rename -n 's/[\.-]*(\d{2})\.(\d{2})\.(\d{2})/-20$1$2$3/; s/^-//' {} \;
```
Just remove the -n.

Is that what you wanted? I'm not sure.

---

### Post by altonbr on 2007-09-17
First of all, I'd like to say that I laughed out loud when I finally read your name last night; Bashologist, "No wonder he's so apt at helping me!", I exclaimed.

Thanks for your help first of all.

I've tested:

```
rename -n 's/[\.-]*(\d{2})\.(\d{2})\.(\d{2})/-20$1$2$3/; s/^-//' *
```

in multiple directories and they all seem to work perfectly. I'll keep testing, but all looks well!

So if I run this:

```
find -type f -exec rename -n 's/[\.-]*(\d{2})\.(\d{2})\.(\d{2})/-20$1$2$3/; s/^-//' {} \;
```

It will run recursively through my whole home directory correct? (So long as I run it from my home directory of course). Can I first get some help understanding what it's doing? I surprisingly understand most if not all of your Perl regex, but not 'find -type f -exec' ... and how it's working without piping. Then finally, what ' {} \;' is doing.

I'll keep researching.

---

### Post by bashologist on 2007-09-17
> **altonbr said:**
> First of all, I'd like to say that I laughed out loud when I finally read your name last night; Bashologist, "No wonder he's so apt at helping me!", I exclaimed.

Thanks for your help first of all.

Your welcome. n_n

> **altonbr said:**
> It will run recursively through my whole home directory correct? 
Yep, even hidden directories, which may not be what you want.

> **altonbr said:**
> Can I first get some help understanding what it's doing? I surprisingly understand most if not all of your Perl regex, but not 'find -type f -exec' ... and how it's working without piping. Then finally, what ' {} \;' is doing.

I'll keep researching.

This rename command is really amazing and I think it's a perl program using eval so it works as you would expect, it's great, I love it! The man page explains find better than I ever could.

> **man find]-exec command {} +
[indent]This variant of the -exec option runs the specified command on the selected files, but  the  command  line  is built  by appending each selected filename at the end said:**
> 

> **man find]-exec command  said:**
> All following arguments to find are taken to be arguments to the command until an argument consisting of &#8216;;&#8217; is encountered.[/indent]
You can do some neat things with find. It's very useful, and one of my favorite commands. n_n

---

### Post by altonbr on 2007-09-18
Thanks once again eh? I see what you're doing. Very sharp.

I ran this:

```
find -type f -exec rename -n 's/[\.-]*(\d{2})\.(\d{2})\.(\d{2})/-20$1$2$3/; s/^-//' {} \;
```

and noticed it was renaming things in my personal perferences, such as .nautilus and .gnome, which I don't believe should happen. So going into hidden directories is not needed.

Also, for a file named 'tomshardware-cpu-2006.07.03.03.png', it was renamed as 'tomshardware-cpu-20-20060703.03.png'. It really should have been 'tomshardware-cpu-2006-20070303.png'. I thought the regex would only change files that were contained xx.xx.xx and concatenated a 20 to the first xx. 

I'm quite sure this file naming convention is quite rare and shouldn't be encountered too often.

Lastly, it looks like I have a 'few', but not a lot, of files that are named as 'ad_examples.2006.07.13' which are then renamed to 'ad_examples.20-20060713'. Can we fix that too?

I think I'm just getting too picky now aren't I?

So for that, would I take out that one asterick to make sure that it is either a . or a - infront of the 3 sets of two digit numbers? So it only renames xx.xx.xx?

```
find -type f -exec rename -n 's/[\.-](\d{2})\.(\d{2})\.(\d{2})/-20$1$2$3/; s/^-//' {} \;
```

I could then run a separate regex for the ones that are xxxx.xx.xx.

```
find -type f -exec rename -n 's/[\.-](\d{4})\.(\d{2})\.(\d{2})/-$1$2$3/; s/^-//' {} \;
```

---

### Post by ghostdog74 on 2007-09-18
try this, if you have gawk and give the full path:
```

find $fullpath -type f -name "*.xcf" | awk '/\.[0-9][0-9]\.[0-9][0-9]/{
         b = gensub(/([0-9][0-9])\.([0-9][0-9])\.([0-9][0-9])/,"20\\1\\2\\3","g")
         cmd = "mv " "\047" $0 "\047" " " "\047" b "\047"
         print cmd
         #system(cmd)  #uncomment to rename file
}' 

```

---

### Post by altonbr on 2007-09-22
Thanks ghostdog74 and bashologist, I'll look over and research the scripts you gave me, or simply run bashologist's script on a per-directory basis.

I appreciate everyone's assistance and I'm sorry for being so needy. You lead me in the correct direction and now I'll start doing my part by learning.

Thanks once again!

---

### Post by altonbr on 2007-11-10
Well I ended up writing a PHP-CLI script since that's what I'm most comfortable with. It doesn't read recursively but does exactly what Bashologist suggested and I understand it.

```
<?php

/* ===============================
	Rename files using Perl regex
   =============================== */

function renameFiles ($dir, $pattern, $replacement, $test){
	// TODO: currently has problems with 'never-2007.60.54.txt' as it renames as 'never-2020076054.txt'

	// open a handle to the directory
	$handle = opendir($dir);

	// read all files opened in $handle
	while (false != ($file = readdir($handle))) {
		// evaluate each entry, excluding the . & .. entries
		if ($file != '.' && $file != '..' && true == preg_match($pattern, $file)) {
			$newFileName = preg_replace($pattern, $replacement, $file);
			$testPrefix = '-- test: ';
			if ($test == 0){
				rename($file, $newFileName);
				$testPrefix = '';
			}
			echo ("$testPrefix$file renamed as $newFileName\n\r");
		}
	}
}

renameFiles('./', '/(\d{2})\.(\d{2})\.(\d{2})/', '20$1$2$3', 1);

?>
```

I'm not sure how to run a function on the command line along with the file name, so you'll have to edit the function at the bottom of the code yourself.

---

