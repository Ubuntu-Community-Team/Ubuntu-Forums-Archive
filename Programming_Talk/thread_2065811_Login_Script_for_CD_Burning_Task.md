---
title: "Login Script for CD Burning Task"
date: 2012-10-02
forum: Programming Talk
---

### Post by Ryan79 on 2012-10-02
Hey all :)

so... my project this time is a little different:

I'm creating a login that will run the following script at logon (adding it to .bash_login file after scripts are finished):

```

#!/bin/bash
echo "What would you like to do?"
echo "Press "n" to burn a normal Products CD
echo "Press "r" to burn a RACE Products CD
echo "Press "q" to quit and logout

read REPLY
  if [ "$REPLY" == "n" ]; then
     sh /home/cdburn/Normal_CD.sh
     command clear
  elif [ "$REPLY" == "r" ]; then
     sh /home/cdburn/Race_CD.sh
     command clear
  elfi [ "$REPLY" == "q" ]; then
     break
  fi
done
kill -HUP $PPID

```

the Normal_CD.sh and Race_CD.sh scripts perform correctly by themselves, but when calling the scripts from this one I get an error that states the following:

/home/cdburn/Normal_CD.sh: 19: [: y: unexpected operator

for reference, one of the scripts it's calling is as follows:

```

#!/bin/bash

## setting variables

SOURCE="/dir/to/source/files"
ISO="/dir/to/store/ISO/file"

## Generating ISO file based on Source

rm $ISO
genisoimage -r -J -o $ISO $SOURCE
command clear

## Starting Burn Process

While true; do
     echo "Has a blank CD been inserted? (y/n): "; read REPLY;
     if [ "$REPLY" == "n" ]; then
          wodim -eject
          command clear
          echo Please insert a blank disk

     elif [ "$REPLY" == "y" ]; then
          wodim -v -eject dev=dev/sg1 -data $ISO;
          break
     fi
done
command clear

while true; do
     echo "Do you wish to burn another? (y/n): "; read REPLY;
     if [ "$REPLY" == "y" ]; then
          command clear
          echo "waiting 5 seconds for a blank disk"
          sleep 5
          command clear
          wodim -v -eject dev=/dev/sg1 -data $ISO
          command clear
     elif [ "$REPLY" == "n" ]; then
          break
     fi
done
echo "Returning to Main Menu"

```

Any ideas on why the Normal_CD.sh would break when getting called from the login.sh?

Thanks for the help!

---

### Post by Ryan79 on 2012-10-02
as a side note... I'll probably add another option on the main menu to generate the ISO there, instead of the burning scripts creating the iso... and I'll set something in the login script to state the date/time the ISO was generated...

but I wanted it to work this way first, with the core functions working, before I tweak it more ;)

---

### Post by spjackson on 2012-10-03
Are you sure that the code you have posted is **exactly** what you are running?

I ask this because the first script has elfi when it should be elif, and it has break and done but no while. The second script has While with a capital W.

It is hard for others to spot the real issue if the code you have posted is only a vague approximation to what you are running.

> 
/home/cdburn/Normal_CD.sh: 19: [: y: unexpected operator

This implies a fault on line 19 of /home/cdburn/Normal_CD.sh, but in the absence of true code, I wouldn't like to guess what that fault might be.

---

