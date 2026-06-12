---
title: "Lazy shell script? :D"
date: 2013-02-08
forum: Programming Talk
---

### Post by Jamie_Edwards on 2013-02-08
Hi guys,

I've made four scripts already that have done as I've asked one being named "clean.sh" which is used to clean three directories of .o, .bin and .iso files ( there is a reason why I've had to make this script ).

The second is called "update_image.sh" which makes a bootable .iso file for me to run in bochs ( using the stage2_eltorito image ).

The third is called "run_bochs.sh" which as it's title says, it runs bochs.

The fourth is called "run.sh" which has commands that initiate update_image and run_bochs in that order.

The only thing is I've decided to become "lazy" and I'm starting to get fed up of having to write
```

sh clean.sh
make
sh run.sh

```

all the time. I want to actually be able to initiate run.sh and it execute the commands contained in clean.sh, initiate make and if there are no errors it then execute the commands in update_image and then run_bochs.

If there are errors in make however, I want it to stop there and then.

My question is, how do I go about it? How do I tell it to stop if it finds errors ( although I want it to still carry on if there are warnings though )?

The rest I can fill in :D

Thank you

---

### Post by schragge on 2013-02-08
At least, you can put the target *clean* into your makefile that invokes *clean.sh*
```

…
all: clean …
…
clean:
	./clean.sh
…

```That's one command less to type.

---

### Post by Jamie_Edwards on 2013-02-08
> **schragge said:**
> At least, you can put the target *clean* into your makefile that invokes *clean.sh*
```

…
all: clean …
…
clean:
	./clean.sh
…

```That's one command less to type.

That doesn't work, it's coming up with a permission denied error.

Also, the reason I'm using clean.sh instead of make clean is because for some reason it isn't working anymore. When I invoke it, it only cleans the iso directory which is the last of the three directories. My clean command is:

```

.PHONY: clean

clean:
    @echo "\tAbout to clean following directories:"
    -rm obj/*.o, \
    kern/*.bin, \
    iso/*.iso
    @echo \tDirectories clean. Continuing..."

```

And there is a tab space before each of the directories not 4 spaces as in the code above.

---

### Post by r-senior on 2013-02-08
Makefiles usually need rm -f because there's no opportunity to prompt for removal. Be very careful that you test this on a backup copy because any use of rm -f is potentially dangerous.

I don't think you want the commas either. I think the command should be:

```
rm -f obj/*.o kern/*.bin iso/*.iso
```

You can try this with a test version:

```
$ touch file{1..3}.txt
$ ls
file1.txt  file2.txt  file3.txt
$ rm -f file1.txt, file2.txt, file3.txt
$ ls
file1.txt  file2.txt
$ rm -f file1.txt file2.txt file3.txt
$ ls
$ 

```

EDIT: Testing this with a Makefile:

```
$ ls
iso  kern  Makefile  obj
$ touch obj/test{1..3}.o
$ touch kern/test{1..3}.bin
$ touch iso/test.iso
$ ls -R
.:
iso  kern  Makefile  obj

./iso:
test.iso

./kern:
test1.bin  test2.bin  test3.bin

./obj:
test1.o  test2.o  test3.o
$ cat Makefile
all: clean

clean:
	rm -f obj/*.o kern/*.bin iso/*.iso
$ make clean
rm -f obj/*.o kern/*.bin iso/*.iso
$ ls -R
.:
iso  kern  Makefile  obj

./iso:

./kern:

./obj:
$ 

```

---

### Post by Bachstelze on 2013-02-08
> **r-senior said:**
> Makefiles usually need rm -f because there's no opportunity to prompt for removal. Be very careful that you test this on a backup copy because any use of rm -f is potentially dangerous.

No, not at all. Makefiles usually use rm -f so that trying to rm a nonexistent file will not cause an error:

```
firas@aoba ~ % rm foo
rm: foo: No such file or directory
firas@aoba ~ % rm -f foo
firas@aoba ~ % 

```

Using rm -f is no more dangerous that just rm if you don't run it as root.

---

### Post by r-senior on 2013-02-08
You are absolutely right. I wonder where I got that idea from?

---

### Post by Jamie_Edwards on 2013-02-08
> Makefiles usually need rm -f because there's no opportunity to prompt for removal. Be very careful that you test this on a backup copy because any use of rm -f is potentially dangerous.

I was actually using that before this happened but I removed the -f to find out if there were any errors of which it was complaining that the obj/ and kern/ directives were didn't exist.

Upon removing the comma's it removed everything fine. So that works and I can now removed clean.sh from the project.

That being said, I still want to try and get a script that I can invoke and it does everything inside it and stop if there is an error in make?

---

