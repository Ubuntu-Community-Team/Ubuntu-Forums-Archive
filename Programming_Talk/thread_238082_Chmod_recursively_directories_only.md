---
title: "Chmod recursively directories only?"
date: 2006-08-17
forum: Programming Talk
---

### Post by Aurdal on 2006-08-17
So, I accidentally(I had a stupid-moment) chmodded my home dir to 777 recursively. Since I have no executables in there as far as I know, I chmodded it again recursively to 644. However directories must have the execute so I wrote this perl script to chmod only directories:

```
#! /usr/bin/perl

format MYFORMAT =
Chmod 755 @<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<  @<<<<<
$dir[$i], $succ_2
.

$mode = 0755;

$~ = "MYFORMAT";

@path_arr = split(/\//, $0);
for ($j = 0; $j < @path_arr; $j++)
{
	if ($path_arr[$j] ne "chmod.pl")
	{
		if ($j != 0)
		{
			$path .= "\/";
		}
		$path .= $path_arr[$j];
	}
}

opendir(MYDIR, "$path");

@dir = readdir (MYDIR);

for ($i = 0; $i < @dir; $i++)
{
	if (-d $dir[$i] && $dir[$i] ne "." && $dir[$i] ne "..")
	{
		$success = chmod ($mode, $dir[$i]);
		if ($success)
		{
			$succ_2 = "Ok";
			write;
		}
		else
		{
			$succ_2 = "Failed";
			write;
		}
	}
}
```

However, this is not recursive, so I'ts not really useful. So is there anyway to make it recursive, or a way to chmod only directories from the shell, or some other way to solve my problem?

Thanks.
-Kristoffer Aurdal

---

### Post by tseliot on 2006-08-17
I'm moving this thread to the Programming talk

---

### Post by ifokkema on 2006-08-17
My guess it that it's easier to use chmod in combination with find;
chmod 644 `find ~ -type d`

---

### Post by MacMan on 2006-08-17
> **Aurdal said:**
> or a way to chmod only directories from the shell

I think **find** can help you. I tried this in a shell:
```

find . -type d -exec chmod 755 \{\} \;

```
and it seems to do what you need. Just cd in the directory where you want to start from first.

I hope this helps.
Ciao.
-- 
Mac

---

### Post by LordHunter317 on 2006-08-17
All of that is excessive.

In this case, it would have been safe to target directories via 'X' (not, only after doing the global 644 change, not after 777):```
chmod -R u=rwX,g=rX,o-rwx
```would work. Note 'x' and 'X' have different meanings.

---

### Post by ifokkema on 2006-08-17
> **LordHunter317 said:**
> In this case, it would have been safe to target directories via 'X' (note, only after doing the global 644 change, not after 777):```
chmod -R u=rwX,g=rX,o-rwx
```would work. Note 'x' and 'X' have different meanings.
Nice... I had quickly scanned the chmod man pages before posting, looking for an argument related to file types, but missed that option, as it's explained within the description.

---

### Post by LordHunter317 on 2006-08-17
Also, you made one mistake I missed reading this thread.  Never, ever use `` with unbounded output unless you like crashing your shell.

---

### Post by ifokkema on 2006-08-17
Ah, I see it done all the time, but I had noticed some commands refusing to run, spawning a "argument list too long" or the like. Good to know.

Before, I used '(...) | xargs (...)' which is just a little more typing.

---

### Post by LordHunter317 on 2006-08-17
> **ifokkema said:**
> Ah, I see it done all the time, but I had noticed some commands refusing to run, spawning a "argument list too long" or the like. Good to know.Bash will normally manage to do that.  However, dumber shells and shells on other OSes will frequently just crash.

> Before, I used '(...) | xargs (...)' which is just a little more typing.That works for many situations.  xargs is a very important tool.  The other thing that works if you need to do more arbitrary processing is:```
command | while read line ; do
    # commands
done
```The only catch here is that in bash, both sides of the pipe are in subshells.  This means that if you change any global variables inside the loop, the change will not be captured outside the loop.  However, you cannot rely on this behavior.  The posix shell standard allows the last command in a pipeline to be run in the current shell.  In ksh, changes to global variables inside the loop will be seen outside the loop.

There's your obscure shell lesson for the day.

---

### Post by ifokkema on 2006-08-17
> **LordHunter317 said:**
> There's your obscure shell lesson for the day.
Thanx :)

---

