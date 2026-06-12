---
title: "Need some help with further bash scripting."
date: 2008-06-30
forum: Programming Talk
---

### Post by _UsUrPeR_ on 2008-06-30
Here's what the following code does:

1: mounts a VMware server windows directory resident on the hard drive
2: create .iso of the windows directory
3: burn that .iso's data to cd
4: delete client medical information on Windows directory
5: move .iso to hidden directory on the ubuntu partition in case of emergency, while changing the name to the date and time it was burned to stop over-writing
6: unmount the vmware directory


```
#!/bin/bash

Pause()
{
  key=""
  echo -n Press and key to continue burning the CD...
  stty -icanon
  key=`dd count=1 2>/dev/null`
  stty icanon
}
ANSWER2=n

echo
echo "Ensure there is a single test in the twindata drive."
echo "Everything in the twindata drive will be written to CD."
echo
Pause
echo

mount /home/remote/twindata
mkisofs -o cd.iso -R -joliet-long /home/remote/twindata
rdrecord dev=/dev/sg0 -vvv -data -force -eject /gome/remote/cd.iso
umount /home/remote/twindata

echo
echo
echo -n "VERIFY THAT THE CD WORKS IN ANOTHER COMPUTER."
echo
echo -N "Did you make the CD correctly? (y/n)"

read ANSWER

if [ "$ANSWER" == "y" ]
then
mount /home/remote/twindata
rm -rf /home/remote/twindata/*
mv /home/remote/cd.iso /home/remote/burned/`date +%F'-'%R`.iso
umount /home/remote/twindata
fi

while [ "$ANSWER" != "y" ]
do
  while [ "$ANSWER2" != "y" ]
  do
    echo
    echo "In Windows, try to fix any issues you have with"
    echo "the CD that was created."
    echo
    Pause

    mount /home/remote/twindata
    mkisofs -o cd.iso -R -joliet-long /home/remote/twindata
    rdrecord dev=/dev/sg0 -vvv -data -force -eject /gome/remote/cd.iso
    umount /home/remote/twindata

    echo
    echo
    echo -n "Did this CD work better for you? (y/n)"
    read ANSWER2

    if [ "$ANSWER2" == "y" ]
    then
      mount /home/remote/twindata
      mv /home/remote/cd.iso /home/remote/burned/`date +%F'-'%R`.iso
      rm -rf /home/remote/twindata/*
      umonut /home/remote/twindata
      exit
    fi
  done
done

```

What I am looking for is a way to ensure that the individual burning the CD is only burning one patient file at a time. I need some way to count the number of directories in the mounted Windows directory, and put them in the script in order to stop the user from burning before fixing the mistake.

To illustrate in simple words:

```
1 - mount windows directory
2 - check to see how many directories are to be burned in the windows directory
3 - if there is more than one directory to be burned, spit out error and ask user to check the windows directory

```

I am not sure what I could use to enumerate the number of directories, nor am I familiar with instantiating a variable or string with the retrieved information once I have it.

Any help would be appreciated.

---

### Post by geirha on 2008-06-30
Something like this?
```

dirs=0
for file in /home/remote/twindata/* ; do
  [ -d "$file" ] && ((dirs++))
done
echo $dirs directories in /home/remote/twindata/

```

---

### Post by _UsUrPeR_ on 2008-06-30
Yes. Something exactly like that. Thank you very much. You are a gentleman and a scholar.

---

### Post by ghostdog74 on 2008-06-30
using find and wc
```

find /home/remote/twindata/* -type d | wc -l

```

---

### Post by _UsUrPeR_ on 2008-07-02
Welp, the boss wants more now. Here's what I currently have, and it works perfectly.

```
#!/bin/bash

#Begin Pause method
Pause()
{
	key=""
	echo -n "Press any key to continue burning the CD..."
	stty -icanon
	key=`dd count=1 2>/dev/null`
	stty icanon
}
#End Pause Method

#Begin Dircount Method
Dircount()
{
mount /home/remote/twindata

		for file in /home/remote/twindata/* ; do	#this counts the amount of directories in twindata
			[ -d "$file" ] && ((dirs++))
		done

		while [ "$dirs" != 1 ]				#If the directory is not by itself, this will present an error
		do
			echo
			dirs=0
				for file in /home/remote/twindata/* ; do
				[ -d "$file" ] && ((dirs++))
			done
			if [ "$dirs" != 1 ]
			then
				echo $dirs "FOLDERS IN TWINDATA. THERE IS MORE THAN ONE PATIENT FILE IN THERE."		
				echo "Please remove extra patient files and try again."	
				Pause
			fi
		done

umount /home/remote/twindata
}
#End Dircount method

#Begin CD Burning method
Burn()
{
mount /home/remote/twindata
mkisofs -o cd.iso -R -quiet -joliet-long /home/remote/twindata
cdrecord dev=/dev/sg0 -data -s -force -eject /home/remote/cd.iso
umount /home/remote/twindata
}
#End CD Burning method

#Begin old file disposal method
Dispose()
{
mount /home/remote/twindata
rm -rf /home/remote/twindata/*
mv /home/remote/cd.iso /home/remote/burned/`date +%F'-'%R`.iso
umount /home/remote/twindata
exit
}
#End old file disposal method


#Begin initial variable declaration
ANSWER2=n
dirs=0
#End initial variable declaration

echo
echo "Ensure there is a single test folder in the twindata drive."
echo
Pause
echo

Dircount
Burn

echo
echo
echo -n "VERIFY THAT THE CD WORKS IN ANOTHER COMPUTER."
echo
echo -n "Did you make the CD correctly? (y/n)"

read ANSWER

if [ "$ANSWER" == "y" ]
then
Dispose
fi

while [ "$ANSWER" != "y" ]
do
	while [ "$ANSWER2" != "y" ]
	do
		echo
		echo "Ok, well go in to Windows and try to fix"
		echo "any problems that you have recognized."
		echo
		Pause
		
		Dircount		
 		Burn

		echo
		echo
		echo -n "Did this CD work better for you? (y/n)"
		read ANSWER2
		
		if [ "$ANSWER2" == "y" ]
			then
			Dispose
			fi
	done
done


```

Now, he's looking for a menu option. Actually, I mean to say that instead of causing an issue over the amount of directories listed, he would prefer to work with them.

I am totally lost as to how to do the following, and it may result in myself learning how to use another programming language, but for the moment, I am intrigued as to how it could be done in bash.

here's what he wants:
Instead of printing out an error pertaining to too many directories in the directory to be burned, he would like to offer a choice of which directories to burn.

As an example:

```
User clicks on this script

Program alerts user to the number of directories above one (I already have this working)

Program prints out directory names, and enumerates them, asking the user which directory they would like to burn to CD.

When the user selects, the program burns only that directory, then goes on to delete the patient files, per normal
```

The part that gets me is my lack of knowledge on array functions. Is this even something that requires an array? Can bash coding even handle arrays?

---

### Post by ghostdog74 on 2008-07-02
Please do read the bash guide in my sig when you are free. It contains almost everything you need to meddle with bash, with examples too. 
1) for creating menus:  a) you can use select : see [here]("http://www.tldp.org/LDP/abs/html/testbranch.html") or
   b) if your environment has zenity 

2) If you want to use arrays: see [here]("http://tldp.org/LDP/abs/html/arrays.html")

3) 
> Is this even something that requires an array
arrays are useful when you want to use the data stored in various parts of the script, ie for later use.It all depends on your program design

4) > Can bash coding even handle arrays
see 2)

---

### Post by _UsUrPeR_ on 2008-07-02
hah! Thanks. I didn't even notice you had tutorials in your sig. I'll take a look!

---

### Post by _UsUrPeR_ on 2008-07-03
Thank you both for your help again. With the tutorial, i was able to get everything the way the boss wanted it!

Here's the results:

```
#!/bin/bash

Pause()
{
        key=""
        echo -n "Press any key to exit..."
        stty -icanon
        key=`dd count=1 2>/dev/null`
        stty icanon
}


Select()
{
	mount /home/remote/twindata
	echo
	i=0
	for file in /home/remote/twindata/* ; do
	let "i=$i+1"
	dirs[$i]=$file

	if [ "$file" == "/home/remote/twindata/*" ]
		then
		echo "There is no patient data in twindata drive."
		echo
		umount /home/remote/twindata
		Pause
		exit
	fi

	echo "[$i] $file"
	done
	echo
	echo "Which directory would you like to burn?"
	echo -n "Please select the number you would like to burn. (1 - $i):"
	read ANSWER
	umount /home/remote/twindata
}

Burn()
{
	mount /home/remote/twindata
	mkisofs -o cd.iso -R -quiet -joliet-long ${dirs[$ANSWER]}
	cdrecord dev=/dev/sg0 -data -force -eject /home/remote/cd.iso
	umount /home/remote/twindata
}

Dispose()
{
	mount /home/remote/twindata
	rm -rf ${dirs[$ANSWER]}
	mv /home/remote/cd.iso /home/remote/burned/`date +%F'-'%R`.iso
	umount /home/remote/twindata
}


ANSWER2=y
while [ "$ANSWER2" != "n" ]
do
	Select
	Burn
	Dispose

	echo
	echo
	echo -n "WOULD YOU LIKE TO BURN ANOTHER PATIENT FILE? (y/n): "
	read ANSWER2
done

```

Thanks again.

---

### Post by geirha on 2008-07-03
> **joelkillspeople said:**
> Thank you both for your help again. With the tutorial, i was able to get everything the way the boss wanted it!

Here's the results:

I looks like a useful script to me! Though since you have posted the resulting script here, I thought I'd give you some comments and suggestions for improvements. I hope you consider it constructive criticism :)

> **joelkillspeople said:**
> ```

Pause()
{
        key=""
        echo -n "Press any key to exit..."
        stty -icanon
        key=`dd count=1 2>/dev/null`
        stty icanon
}

```
This function can be done on one line
```
Pause() { read -s -n1 -p "Press any key to continue..." key; }
``` Doesn't do exactly the same thing, but close. The builtin read command doesn't have its own man-page, instead it is documented inside bash's man-page. That's a bit unfortunate since it makes it hard to find. Google is helpful though: [http://www.ss64.com/bash/read.html](http://www.ss64.com/bash/read.html)

> **joelkillspeople said:**
> ```

Select()
{
	mount /home/remote/twindata
	echo
	i=0
	for file in /home/remote/twindata/* ; do
	let "i=$i+1"
	dirs[$i]=$file

	if [ "$file" == "/home/remote/twindata/*" ]
		then
		echo "There is no patient data in twindata drive."
		echo
		umount /home/remote/twindata
		Pause
		exit
	fi

	echo "[$i] $file"
	done
	echo
	echo "Which directory would you like to burn?"
	echo -n "Please select the number you would like to burn. (1 - $i):"
	read ANSWER
	umount /home/remote/twindata
}

```
That if-expression, **if [ "$file" == "/home/remote/twindata/*" ]**, will most likely never return true, unless you have a directory named the literal *. Try checking the number of elements in your dirs array instead, by using ${#dirs[@]} or ${#dirs[*]}
```

    i=0; dirs=( )   # ( ) makes $dirs an empty array.       
    for file in /home/remote/twindata/* ; do
        ((i++))
        dirs[i]="$file"
        echo "[$i] $file"
    done
    if [ ${#dirs[@]} == 0 ]; then
        echo "There is no patient data in twindata drive."
        exit
    fi

```
> **joelkillspeople said:**
> ```

Burn()
{
	mount /home/remote/twindata
	mkisofs -o cd.iso -R -quiet -joliet-long ${dirs[$ANSWER]}
	cdrecord dev=/dev/sg0 -data -force -eject /home/remote/cd.iso
	umount /home/remote/twindata
}

```
This looks good, though it probably won't hurt to to check the return values of mkisofs and cdrecord. The following (notice the &&) will only run cdrecord if mkisofs completed successfully, and if cdrecord also completed successfully, a (success) message is written. If either fails, it quits so that the Dispose function won't delete the file when it hasn't been burned.
```

Burn()
{
	mkisofs -o cd.iso -R -quiet -joliet-long "${dirs[$ANSWER]}" &&
	cdrecord dev=/dev/sg0 -data -force -eject /home/remote/cd.iso
        if [ $? == 0 ]; then
             echo "CD burning successful
        else
             echo "CD burning failed. Aborting"
             exit 1
        fi
}

```
The special variable $? contains the return value of the last run command, and 0 means true, everything else means false.
> **joelkillspeople said:**
> ```

ANSWER2=y
while [ "$ANSWER2" != "n" ]
do
	Select
	Burn
	Dispose

	echo
	echo
	echo -n "WOULD YOU LIKE TO BURN ANOTHER PATIENT FILE? (y/n): "
	read ANSWER2
done

```
You seem to be running mount and umount alot. That's a bit unnecessary in my opinion. You should just mount it at the start, and then umount it when you exit. You seem to have an umount at all exit points, but you can add a trap that will run the umount command if you exit at any place in the file, even if you hit Ctrl+C to interrupt the script. So I would do something like this at your "main()" part:
```

if ! mount /home/remote/twindata; then  # Try mounting, and if it fails:
    echo "Failed to mount /home/remote/twindata"
    exit 1
fi
trap 'umount /home/remote/twindata && echo /home/remote/twindata unmounted' EXIT
ANSWER2="y"
while [[ "$ANSWER2" =~ [Yy] ]]; do
   ...

```

---

### Post by _UsUrPeR_ on 2008-07-09
Next question: how do I do this in a GUI instead of a text window?

I started in on creating one with glade, but can't really see where/how I would get this to jive with bash commands. Even more confusing, it would make the most sense to have this use radio buttons to allow the user to only select one patient, but I can't figure out how I would have a variable amount of radio buttons based on the number of directories present at a given time. I have put together how I want the menu to look with glade here:

```
<?xml version="1.0" encoding="UTF-8" standalone="no"?>
<!DOCTYPE glade-interface SYSTEM "glade-2.0.dtd">
<!--Generated with glade3 3.4.5 on Tue Jul  8 15:21:42 2008 -->
<glade-interface>
  <widget class="GtkWindow" id="window1">
    <child>
      <widget class="GtkVBox" id="vbox1">
        <property name="visible">True</property>
        <child>
          <widget class="GtkLabel" id="label1">
            <property name="visible">True</property>
            <property name="label" translatable="yes">label</property>
          </widget>
          <packing>
            <property name="position">1</property>
          </packing>
        </child>
        <child>
          <widget class="GtkHBox" id="hbox1">
            <property name="visible">True</property>
            <child>
              <widget class="GtkRadioButton" id="radiobutton1">
                <property name="visible">True</property>
                <property name="can_focus">True</property>
                <property name="label" translatable="yes">radiobutton</property>
                <property name="response_id">0</property>
                <property name="active">True</property>
                <property name="draw_indicator">True</property>
              </widget>
            </child>
            <child>
              <widget class="GtkVScrollbar" id="vscrollbar1">
                <property name="visible">True</property>
                <property name="adjustment">0 0 100 1 10 10</property>
              </widget>
              <packing>
                <property name="position">1</property>
              </packing>
            </child>
          </widget>
          <packing>
            <property name="position">-1</property>
          </packing>
        </child>
        <child>
          <widget class="GtkHBox" id="hbox2">
            <property name="visible">True</property>
            <property name="spacing">51</property>
            <child>
              <placeholder/>
            </child>
            <child>
              <widget class="GtkButton" id="button1">
                <property name="visible">True</property>
                <property name="can_focus">True</property>
                <property name="receives_default">True</property>
                <property name="label" translatable="yes">button</property>
                <property name="response_id">0</property>
              </widget>
              <packing>
                <property name="position">1</property>
              </packing>
            </child>
            <child>
              <widget class="GtkButton" id="button2">
                <property name="visible">True</property>
                <property name="can_focus">True</property>
                <property name="receives_default">True</property>
                <property name="label" translatable="yes">button</property>
                <property name="response_id">0</property>
              </widget>
              <packing>
                <property name="position">2</property>
              </packing>
            </child>
            <child>
              <placeholder/>
            </child>
          </widget>
          <packing>
            <property name="position">2</property>
          </packing>
        </child>
      </widget>
    </child>
  </widget>
  <widget class="GtkMenu" id="menu1">
    <property name="visible">True</property>
  </widget>
</glade-interface>
```

It will look nice, but I have this funny feeling that if I had wanted to use a GUI, I should have tried out another programming language. Is there a better way to do this?

---

### Post by mssever on 2008-07-09
> **joelkillspeople said:**
> It will look nice, but I have this funny feeling that if I had wanted to use a GUI, I should have tried out another programming language. Is there a better way to do this?
As far as I know, the only way to use GTK from bash is through zenity. If your needs are beyond what zenity can do, you need to change languages. Note, however, that if your main logic is already written, you might be able to use it as a backend and simply code up the frontend in another language.

---

### Post by _UsUrPeR_ on 2008-07-09
```
As far as I know, the only way to use GTK from bash is through zenity
```

Bummer. Yeah, that's what it looked like. Oh well. I'll give zenity a shot.

Thanks for your help.

---

### Post by ghostdog74 on 2008-07-10
see [here](http://www.gtk-server.org/) too

---

