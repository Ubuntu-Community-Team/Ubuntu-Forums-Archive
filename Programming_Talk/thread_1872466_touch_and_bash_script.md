---
title: "touch and bash script"
date: 2011-10-30
forum: Programming Talk
---

### Post by crownedzero on 2011-10-30
I'm trying to get a single var from a user and then create files based on that, very rudimentary but I can't seem to get it right. 

i.e.
variable ~/make/this.txt ~/file/over/here.txt

should create a this.txt in ~/make and here.txt in ~/file/over/

apparently i'm syntax dumb today ... =(

---

### Post by ofnuts on 2011-10-30
What is the command "variable" supposed to do? And i the command itself is a variable (pretty strange way, quite dangerous), shouldn't it be "$variable"?

---

### Post by crownedzero on 2011-10-30
read files_to_create

touch $files_to_create

I tried using grouping in the script but ended up with braces etc in the file names.

---

### Post by WasMeHere on 2011-10-30
Hi crownedzero,

For example: Make a test directory, 'cd' into it and create subdirectories 'source', 'make' and 'file/here'. Add files into 'source'.
```
for ftc in $(ls source); do touch make/$ftc; touch file/here/$ftc;done
```
Then develop it step-wise until it can do what you want!

Have fun finding out about Ubuntu :-)
Olle

---

### Post by crownedzero on 2011-10-30
That'll work but I'm trying to keep this as simple as possible.

I need the shell to interpret the variable literally, if for example:
$var = ~/dir1/file1

I should be able to touch $var and get my empty file created.

---

### Post by WasMeHere on 2011-10-30
If you want to touch the source, do it like this instead.
```
for ftc in $(ls source); do touch [COLOR="Red"]source[/COLOR]/$ftc; touch file/here/$ftc;done
```

I try to make th shell variable [COLOR="Red"]ftc[/COLOR] represent the [COLOR="Red"]f[/COLOR]ile-[COLOR="Red"]t[/COLOR]o-[COLOR="Red"]c[/COLOR]reate. The source file is touched and an empty file is created. It can be debated if it is simple, but at least it's a one-liner.

---

### Post by lswb on 2011-10-30
Not quite clear on what you are trying to do, but I believe your problem is that you want to create the directory for the desired files at the same time as the files? If so then perhaps some of the parameter expansion capabilities of bash will help. For example ```

$ VAR=Directory/File
$ echo ${VAR#*/}
File
$ echo ${VAR%/*}
Directory
$ 

```

There are several other constructs that are helpful. Use man bash, or even better, google for the "Advanced Bash Scripting Guide"

---

### Post by crownedzero on 2011-10-30
```

echo -e "*****************************************************"
echo -e "**                                                 **"
echo -e "**         Now let's create some files in          **"
echo -e "**    those directories. Please enter the files    **"
echo -e "**   that you would like to create one one line.   **"
echo -e "**        Please include the full directory.       **"
echo -e "**                                                 **"
echo -e "**         ~/dir1/this.txt ~/dir2/makes.txt        **"
echo -e "**                ~/dir3/files.txt                 **"
echo -e "*****************************************************"

read files_to_create

touch ?????

```

If the user enters "~/dir1/file1 ~/dir2/file2" without quotes I want it to create file1 in /home/user/dir1 and file2 in /home/user/dir2.

---

### Post by WasMeHere on 2011-10-30
Try this one

```
echo -e "*****************************************************"
echo -e "**                                                 **"
echo -e "**         Now let's create some files in          **"
echo -e "**    those directories. Please enter the files    **"
echo -e "**   that you would like to create one one line.   **"
echo -e "**        Please include the full directory.       **"
echo -e "**                                                 **"
echo -e "**         ~/dir1/this.txt ~/dir2/makes.txt        **"
echo -e "**                ~/dir3/files.txt                 **"
echo -e "*****************************************************"

read files_to_create
for i in $files_to_create; do mkdir -p ${i%/*};touch $i;done

```

---

### Post by crownedzero on 2011-10-30
As silly as this sounds I'm trying to put together a lesson plans for young kids i'm not sure they'll understand for loops and iterating thru a sequence >.<

---

### Post by lswb on 2011-10-30
If the directories already exist, something like ```

while read FILENAME; do touch $FILENAME; done

```
should work. If the directories don't exist, you have more work to do.

---

