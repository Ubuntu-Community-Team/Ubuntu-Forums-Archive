---
title: "Send SMS through Ubuntu using Bluetooth phone (and automate it using script!)"
date: 2009-06-28
forum: Outdated Tutorials &amp; Tips
---

### Post by Nizar on 2009-06-28
[B]Send SMS through Ubuntu using Bluetooth phone (and automate it using script!) 
[/B]by: Nizar Diamond Ali (nizar.ali@gmail.com)

[B]Introduction
[/B]Mobile phones today serve a number of needs apart from basic voice communication. Even more than it is used for calls, a handset today finds it usage for SMS – Short Messaging Service. SMS brings lots of opportunities such as reaching out to customers in new ways, providing them alerts and status updates about various business services, or even in educational setups announcing important broadcast messages. Though there are some non-free tools available for sending messages through a mobile phone connected with a PC, today this How To guide is going to demonstrate how the same can be done – free of cost – using Ubuntu, along with some basic scripting to automate the process.

[B]Setup to use this guide
[/B]The setup requires a Bluetooth enabled phone, a PC with a Bluetooth adapter running Ubuntu 7.10 or above. This guide has been written and tested with a Sony Ericsson K series phone connected with an Acer laptop. First ensure that the phone is connected with the computer and both are paired. Refer Box 1 for preliminary settings – how to configure a Bluetooth phone in Ubuntu (present at the end of this guide). 

This guide assumes user is logged in as root user.

Commands mentioned are to be entered in Terminal window that can be opened through menu Applications > System Tools > Root Terminal

Create all the files mentioned in this tutorial in same folder as it will be easy to locate them afterwards.

**Step 1 – Check the gsmsendsms command**
The library that is used to access GSM phone access via GMS modem or over infra-red is GSMLIB. Accessing its various programs is quite easy as detailed information is provided in the manual pages. Though there have been some graphical interface programs available, for power users it is always recommended to rely on the basic command line for maximum control and options. The utility that is used for sending SMS is gsmsendsms having following syntax:

[FONT="Courier New"]gsmsendsms -d device-location phone-number SMS-text[/FONT]

Here, the device location for Bluetooth phone would be /dev/rfcomm0
 as shown in sample configuration in Box 1 at the end of this guide. The file /etc/bluetooth/rfcomm.conf is used for binding phone with computer by providing phone address (alpha-numeric code separated by colons like MAC address) and channel number to bind to. Phone number format is the one generally used e.g. 02001234567 followed by the last argument which is the SMS text to be sent.  

This command can be used as:

[FONT="Courier New"]gsmsendsms -d /dev/rfcomm0
 02001234567 “hello”
[/FONT]
Now the problem is if there's a long list of recipients and same message is to be sent across, this command would have to be repeated over and over again with different numbers. To automate this, a simple script can be written that reads recipient numbers from a text file and text messages from another text file. Create two files list.txt and msg.txt for this, respectively for recipient list (enter one phone number per line, only 1 number would do for testing purposes) and text messages (only 1 message in this file would do for testing purposes). These files will be used in sample scripts shown below. Keep all these files in the same folder so that complete path names are not required in the commands.

**Step 2 – Create a script to read phone numbers from a text file**
Start off with a simple script that reads numbers and then the functionality of sending SMS will be added. Create a new file and name it read1.sh and make it executable by right clicking over it and selecting “Allow executing file as program” in Permissions tab. Here is the script file:

[FONT="Courier New"]FILELIST=$1

while read NUMBER

do 

echo $NUMBER

done < $FILELIST

[/FONT]
This script takes a command line argument denoted by $1 sign (which would be the file name list.txt created above) and stores it in variable FILELIST and then reads line by line from the file storing each line in the variable NUMBER until the file is finished. Every line read is displayed through the Echo command. Execute this file by simply entering its name preceded by dot and forward slash and file name (all without spaces), as that's how scripts are executed, i.e.:

[FONT="Courier New"]./read1.sh list.txt[/FONT]

[B]Step 3 – Create a script to send SMS to numbers present in the text file
[/B]Now let's improve this file further by making it send SMS to these numbers. This requires a text to be sent, and that is going to be provided as second command line argument stored in variable TEXT, and device name is also required which will be stored in variable DEVICE. Here's the script:

[FONT="Courier New"]FILENAME=$1

TEXT=$2

DEVICE=/dev/rfcomm0


while read NUMBER

do 

gsmsendsms -d $DEVICE $NUMBER $TEXT

echo $NUMBER

sleep 1

done < $FILENAME

[/FONT]
Note that the first two lines are two command line arguments denoted by $1 and $2 respectively, and there's a sleep command to give a pause between successive SMS as device takes a while – about a second – to send SMS. Also, take a look at the SMS sending command and compare it as tested earlier over command line. All 3 arguments (device, phone number and SMS text) have now been substituted by variables defined in the script. This script is to be executed as: 

[FONT="Courier New"]./read2.sh file.txt “Hello”[/FONT]

This script now actually automates the process of sending one SMS to a list of recipients. 

[B]Step 4 – Create a script file to read both SMS and phone numbers from text files
[/B]Let's now make use of the text file created earlier that contained SMS text instead of writing the text at command line. Here it goes:

[FONT="Courier New"]FILELIST=$1

FILESMS=$2

DEVICE=/dev/rfcomm0


while read TEXT

do 

echo "Sending..."

echo $TEXT

	while read NUMBER

	do 

	gsmsendsms -d $DEVICE $NUMBER $TEXT

	echo "To..."

	echo $NUMBER

	sleep 1

	done < $FILELIST


done < $FILESMS


[/FONT]
Execute this script as follows:

[FONT="Courier New"]./read3.sh list.txt msg.txt[/FONT]


Along with taking in the list of phone numbers as argument, it also takes in the file where messages are present as second argument. This script makes use of a loop inside a loop (called nested loop) as the first outer WHILE loop reads lines of text in variable TEXT, and for each line of the text read, it starts another inner WHILE loop that reads recipients phone number in variable NUMBER. This inner loop sends the text message to all the numbers present in the phone numbers list, and when it finishes, the control goes back to the outer loop that picks up next next and so on. Such a script can be useful if multiple messages are to be sent to multiple recipients. While creating text files for storing numbers and SMS text, make sure that there are not line breaks at the end as this will create errors while passing them as arguments in SMS sending command. 

Enjoy SMS!


[B]Box 1 - How to configure a Bluetooth phone in Ubuntu
[/B]

**Step 1 – Turn on and test Bluetooth**
Turn on the Bluetooth button or plug-in the adapter. Check the adapter status with:

hciconfig


This results in following output:

root@ubuntu:/# hciconfig

hci0:   Type: USB

        BD Address: 00:19:7E:DF:51:02 ACL MTU: 1017:8 SCO MTU: 64:8

        UP RUNNING PSCAN ISCAN 

        RX bytes:93532 acl:557 sco:0 events:423 errors:0

        TX bytes:28323 acl:389 sco:0 commands:206 errors:0


Or, simply use the following command:

hcitool dev

This results in the following output:

root@ubuntu:/# hcitool dev

Devices:

        hci0    00:19:7E:DF:51:02


In case of error, Bluetooth device may be restarted using the following command:

hciconfig hci0 reset

If settings of Bluetooth are changed, following commands can be used to restart the Bluetooth service:

/etc/init.d/bluetooth restart

**Step 2 – Search the Bluetooth phone**
Turn on the Bluetooth service of the phone, search for phone using the following command:

hcitool scan

This results in the following output – note the phone address (numeric code separated by colon):

root@ubuntu:~# hcitool scan

Scanning ...

        00:1C:A4:96:03:CC       PhoneName


Note down this phone address for future reference. 

**Step 3 – Check for the Bluetooth services available in the phone**
Check for Bluetooth service using the following command:

sdptool browse


This results in list of services and their channel numbers. Note down the DUN – Dial-up Networking service's channel number as this will be required in the next step of editing rfcomm.config file.

**Step 4 – Edit the rfcomm.conf file to enter the phone address and channel number**
Open the following file in Ubuntu's Text Editor. 

/etc/bluetooth/rfcomm.conf


Enter the device name and channel number saved from previous steps in the following section of this file as shown below. 

rfcomm0 { bind yes; device 00:1C:A4:96:03:CC; channel 2; comment "Sony"; }

**Note:** Make a copy of rfcomm.conf file so that it can be restored if required. Use the same method to create backup copies of all the files before editing them.

Backup - Use the following command in Terminal window to create a copy of the file before editing it:
cd/ root
cd etc/bluetooth
cp rfcomm.conf rfcomm.conf-backup


Restore - Use the following commands to first delete the existing file and restore the backup copy
rm  rfcomm.conf
cp rfcomm.conf-backup
 rfcomm.conf

**Step 5 – Set the Bluetooth passcode**
Now enter passcode in the following file for pairing – i.e. the passcode that will have to be entered when computer is searched from the handset and connection is attempted. 

/etc/bluetooth/hcid.conf


Make sure that the file appears as follows:

options {

	autoinit yes;


	security auto;


	pairing multi;


	passkey "1234";


}


**Step 6 – Pair the phone and computer**
Now search the computer from handset, and enter the passkey 1234 when prompted to complete pairing. The phone is now connected with the computer, and its device location is /dev/rfcomm0 as defined above.

---

### Post by rita smith on 2009-09-08
Hi All,

Thanks Nizar, 
This is great to know about sending sms through Ubunutu.****[U] 
[/U]i will definitely try for the same.

Thanks & Keep Sharing!

---

