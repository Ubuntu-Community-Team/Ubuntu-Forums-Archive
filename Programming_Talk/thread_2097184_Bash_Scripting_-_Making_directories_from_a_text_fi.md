---
title: "Bash Scripting - Making directories from a text file"
date: 2012-12-22
forum: Programming Talk
---

### Post by maggotface101 on 2012-12-22
Hey all, I want to make a script that creates directories specified in a user defined text file. If the directory exists in the new users directory, it needs to ask if you want to keep or delete the existing directory, and if you choose to keep it, it'll rename to with the suffix _old (I'm aware that my code for that part is most likely horribly wrong, I'm new to scripting :p). Thing is I don't know how to go around doing this. I looked through the forums and I found some help, but it doesn't seem to work and I keep getting errors with my script, saying the following:
```
./mkusr: line 44: syntax error near unexpected token `else'
./mkusr: line 44: `  else'

```I can't see how my script may have incorrect syntax though. Here is what I have so far, if anyone would be so kind as to share some insight.
```
#!/bin/bash
read -p "Please specify text file of usernames: " usr
if [ ! -f $usr ]
then
  echo "File '$usr' does not exist."
  read -p "Please specify text file of usernames: " usr
fi

echo "File '$usr' loaded successfully."
read -p "Please specify text file of files to copy: " cpy
if [ ! -f $cpy ]
then
  echo "File '$cpy' does not exist."
  read -p "Please specify text file of files to copy: " cpy
fi

echo "File '$cpy' loaded successfully."
read -p "Please specify directory of master copies: " mst
if [ ! -d $mst ]
then
  echo "Folder '$mst' does not exist."
  read -p "Please specify directory of master copies: " mst
fi

echo "Folder '$mst' loaded successfully."
read -p "Please specify directory where new folders will be created: " ndr
if [ ! -d $ndr ]
then
  echo "Folder '$ndr' does not exist."
  read -p "Please specify directory where new folders will be created: " ndr
fi

echo "Folder '$ndr' loaded successfully."

cp $cpy $ndr
echo "Copied '$cpy' to '$ndr' successfully"
cp $usr $ndr
echo "Copied '$usr' to '$ndr' successfully."
cd $ndr

cat $usr | while read -r line
do
  if [ ! -d $line ]
    mkdir $line
  else
    read -p "Directory $line already exists! Would you like to delete the existing directory? Y/N: " yn
    if  [ "$yn" == "y" ]
    then
      rm $line
    else if [ "$yn" == "n" ]
    then
      echo "Renaming existing directory"
      mv $line $line _old
    else
      echo "Unacceptable response. Please press Y/N only."
      read -p "Directory $line already exists! Would you like to delete the existing directory? Y/N: " yn
    fi
  fi
done
```Any help would be greatly appreciated!

---

### Post by trent.josephsen on 2012-12-22
Did you even *look* for a syntax error? Took me about 10 seconds to notice the lack of a "then"

---

### Post by r+9 on 2012-12-22
EDIT: always test your code or you will look silly like me.
I'll be back to work out the bugs.

Just a point of style, I noticed your missing Then just before the line with the error code (line 44).  
I'm also not 100% on the syntax for the ask_user, I might have messed something up.  No time to test while I make breakfast (just enough to write it!)

```
#!/bin/bash

function ask_user() {
	while [[ ! -a $2 || -z $2 ]]  # noexists or is null
	do
		read -p $1 $2
	done
        echo "File: $2 loaded successfully."
}

ask_user "Please specify text for usernames: " usr
ask_user "Please specify text file of files to copy: " cpy
ask_user "Please specify directory of master copies: " mst
ask_user "Please specify directory where new folders will be created: " ndr


cp $cpy $ndr && echo "Copied '$cpy' to '$ndr' successfully"
cp $usr $ndr && echo "Copied '$usr' to '$ndr' successfully."
cd $ndr

cat $usr | while read -r line
do
  if [ ! -d $line ]
  then
    mkdir $line
  else
    read -p "Directory $line already exists! Would you like to delete the existing directory? Y/N: " yn
    if  [ "$yn" == "y" ]
    then
      rm $line
    else if [ "$yn" == "n" ]
    then
      echo "Renaming existing directory"
      mv $line $line _old
    else
      echo "Unacceptable response. Please press Y/N only."
      read -p "Directory $line already exists! Would you like to delete the existing directory? Y/N: " yn
    fi
  fi
done

```

---

### Post by r+9 on 2012-12-22
I've been working with python scripts too much, bash won't return a non integer from a function.

Bash is a great way to get into Linux and scripting, but there is a lot more power in Perl or Python, I'm sure others could plug their preference.

---

### Post by ofnuts on 2012-12-22
> **r+9 said:**
> I've been working with python scripts too much, bash won't return a non integer from a function.

Bash is a great way to get into Linux and scripting, but there is a lot more power in Perl or Python, I'm sure others could plug their preference.
It depends a lot on what you want/need to do. As a glue around individual commands, bash can be a lot quicker to write than python.

---

### Post by maggotface101 on 2012-12-22
> **trent.josephsen said:**
> Did you even *look* for a syntax error? Took me about 10 seconds to notice the lack of a "then"
*facepalm* I just realised my mistake, I feel like an idiot now. >.<

I'll probably be back later to get more help with the rest of it, until then, thanks for the help. :P

> **r+9 said:**
> EDIT: always test your code or you will look silly like me.
I'll be back to work out the bugs.

Just a point of style, I noticed your missing Then just before the line with the error code (line 44).  
I'm also not 100% on the syntax for the ask_user, I might have messed something up.  No time to test while I make breakfast (just enough to write it!)

```
#!/bin/bash

function ask_user() {
	while [[ ! -a $2 || -z $2 ]]  # noexists or is null
	do
		read -p $1 $2
	done
        echo "File: $2 loaded successfully."
}

ask_user "Please specify text for usernames: " usr
ask_user "Please specify text file of files to copy: " cpy
ask_user "Please specify directory of master copies: " mst
ask_user "Please specify directory where new folders will be created: " ndr


cp $cpy $ndr && echo "Copied '$cpy' to '$ndr' successfully"
cp $usr $ndr && echo "Copied '$usr' to '$ndr' successfully."
cd $ndr

cat $usr | while read -r line
do
  if [ ! -d $line ]
  then
    mkdir $line
  else
    read -p "Directory $line already exists! Would you like to delete the existing directory? Y/N: " yn
    if  [ "$yn" == "y" ]
    then
      rm $line
    else if [ "$yn" == "n" ]
    then
      echo "Renaming existing directory"
      mv $line $line _old
    else
      echo "Unacceptable response. Please press Y/N only."
      read -p "Directory $line already exists! Would you like to delete the existing directory? Y/N: " yn
    fi
  fi
done

```

I'll give your code a test and see if I can work from there. If it's not obvious enough already I'm a bit foolish when it comes to programming so I'll probably make more obvious mistakes haha. Thanks anyway though! :D

---

### Post by maggotface101 on 2012-12-27
Back again. Now I've fixed what I needed to fix I'm getting another issue. I thought my code so far was alright, but it's not doing the job. I want the last half of it to read from a text file of usernames and make a directory for each line in it. This is what I have for my text file of usernames while I test it out:

test01
test02
test03
test04 etc.

Any help would be appreciated. :)

---

### Post by Vaphell on 2012-12-27
```
while read -r name
do
  mkdir "$name"
done < names.txt
```

---

### Post by maggotface101 on 2013-01-01
Thanks for the help, it worked up until it finished reading the text file, but then I get this:

```
./mkusr: line 83: syntax error near unexpected token `done'
./mkusr: line 83: `done < $file'
```Here's what I have.

```
while read -r doc
do
  cp $doc ../home/filetransfer
  echo "Copied '$doc' to directory '$ndr/filetransfer'"
done < $copy

cd ../$ndr

file=$ndr

while read -r name
do
  if [ ! -d $name ]
  then
    mkdir $name
  else
    read -p "Directory $name already exists! Would you like to delete the existing directory? Y/N: " yn
    if  [ "$yn" == "y" ]
    then
      rm $name
      mkdir $name
    else if [ "$yn" == "n" ]
    then
      echo "Renaming existing directory"
      mv $name "$name _old"
      mkdir $name
    else
      echo "Unacceptable response. Please press Y/N only."
      read -p "Directory $name already exists! Would you like to delete the existing directory? Y/N: " yn
    fi
  fi
  cp filetransfer $name
  echo "Successfully transferred files to user $name directory."
done < $file
```

Am I overlooking something obvious here? Basically, the code itself needs to create user directories specified in a text file. If it exists, it asks if you want to keep or delete the existing file, and if you choose to keep it, it renames it to <name>_old.
EDIT: Forgot to copy the last part of my script >_< Question still stands though

---

### Post by steeldriver on 2013-01-01
try

> **maggotface101 said:**
> 
```
while read -r doc
do
  cp $doc ../home/filetransfer
  echo "Copied '$doc' to directory '$ndr/filetransfer'"
done < $copy

cd ../$ndr

file=$ndr

while read -r name
do
  if [ ! -d $name ]
  then
    mkdir $name
  else
    read -p "Directory $name already exists! Would you like to delete the existing directory? Y/N: " yn
    if  [ "$yn" == "y" ]
    then
      rm $name
      mkdir $name
    **[COLOR=Red]elif[/COLOR]** [ "$yn" == "n" ]
    then
      echo "Renaming existing directory"
      mv $name "$name _old"
      mkdir $name
    else
      echo "Unacceptable response. Please press Y/N only."
      read -p "Directory $name already exists! Would you like to delete the existing directory? Y/N: " yn
    fi
  fi
  cp filetransfer $name
  echo "Successfully transferred files to user $name directory."
done < $file
```

---

### Post by maggotface101 on 2013-01-02
Thanks a lot, that got the script working, should have no more problems from here onwards. Thanks everyone! :D

---

