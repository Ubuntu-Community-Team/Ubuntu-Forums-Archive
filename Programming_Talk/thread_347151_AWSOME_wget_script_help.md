---
title: "AWSOME wget script help"
date: 2007-01-26
forum: Programming Talk
---

### Post by L14UX_1NS1D3 on 2007-01-26
Hi 
recently I have become interested in shell scripting and out of neccessity I have make a shell script for downloading files from a  txt file stored in a given directory. All the downloaded files would be stored in a specified directory for later viewing. 
heres the code.
___________________________________________________________________________

[B]#!/bin/bash
#
filedir=/home/$user/.batchget/
#
dldir=/home/$user/.batchget/downloads
#
$num=0
#
if [ $filedir = cd $filedir ]
#------------------------------------------------
then
echo "batchget dir found"
#--------------------------------------------------
else
echo "making directory /home/$user/.batchget"
mkdir $filedir
echo "making file batchlog in /home/$user/.batchget"
cat > batchlog
sudo mv /home/$user/batchlog /home/$user/.batchget/batchlog
#------------------------------------------------------------
done
#-------------------------------------------------------
echo "reading batch file"
wget -nc -r -i /home/$user/.batchget/batchlog.txt -p $dldir
echo "completed"
echo "files in /home/"$user"/.batchget/downloads
#
exit
_________________________________[/B]__________________________________________

As you can see this is just a rough draft of the code and surely riddled with errors. I have never done a shell script before and would definitly appreciate feedback on any tips or errors I have made.
thank!

---

### Post by highneko on 2007-01-26
Instead of the test you could use:
mkdir -p "$HOME/.batchget/downloads"

You forgot an "fi". There's no reason for a "done" that I can see. You should use quotes better, for example:
[PHP]echo "files in /home/"$user"/.batchget/downloads"
#should be:
echo "files in /home/$user/.batchget/downloads"
#but I would use the home variable instead of user:
echo "files in $HOME/.batchget/downloads"[/PHP]

---

### Post by L14UX_1NS1D3 on 2007-01-27
thanks so much for the tip!
:D

---

### Post by L14UX_1NS1D3 on 2007-02-03
Ok, heres version 2!
As you can see this is quite an improvement over the latter.
____________________________________________________________________________________________________________

[B]#!/bin/bash
#
filedir=$HOME/.batchget/
#
dldir=$HOME/.batchget/downloads
#
num=0
#
if [ $filedir = cd $filedir ]
#------------------------------------------------
then
echo "batchget dir found"
#--------------------------------------------------
else
echo "creating directory $HOME/.batchget"
sudo mkdir $filedir
sudo chown $USER $filedir
#------------------------------------------------------
fi
#
echo "making file batchlog in $HOME/.batchget"
echo"#type the urls of the files that are to be downloaded" cat > batchlog
sudo mv $HOME/batchlog $HOME/.batchget/batchlog
#------------------------------------------------------------

#-------------------------------------------------------
echo "reading batch file"
wget -c -nc -r -i $HOME/.batchget/batchlog.txt -p $dldir
echo "completed"
echo "files in $HOME/.batchget/downloads"
#
exit 0
[/B]
________________________________________________________________________________________________________

One problem I still have is the "**if [ $filedir = cd $filedir ]**" line, I should problably just make a loop. 
Anyway thats what I have for now, ohh and if anybody has any suggestions  or tip to further the 
development of this script please do so!
thanks.):P

---

### Post by Daveski on 2007-02-03
> **L14UX_1NS1D3 said:**
> One problem I still have is the "**if [ $filedir = cd $filedir ]**" line, I should problably just make a loop.

I use

```
if test -d directoryname
then
 ...
```

which can be written as

```
if [ -d directoryname ]
```

---

### Post by L14UX_1NS1D3 on 2007-02-04
Thanks for the correction!
Getting close to finishing this script!

---

### Post by clouserw on 2007-02-05
Why are you using sudo?  If the files are in your $HOME and you're running the script, chances are good you already have permission to do what you need to do...

---

### Post by L14UX_1NS1D3 on 2007-02-05
I've taken into account all the info I was given on this script and revamped it alittle bit. 
Version 3 should be easer to understand, it looks nicer to me.
____________________________________________________________________________________________________________ 

[B]#!/bin/bash 
#------------------------------------------------------------------
#bash shell script that uses wget to read from a file to
#recursively retrieve urls listed in the txt file.  
#this script will create a hidden directory in your home folder.
#add urls to batchlog.txt file in /home/user/.batchget/.batchlog
#to download files at a certain time or interval use with cron
#------------------------------------------------------------------
#
filedir=$HOME/.batchget/
#
dldir=$HOME/.batchget/downloads
#
#
if [ test -d $HOME/.batchget ] ; then
#------------------------------------------------------------------
echo "batchget dir found"
#------------------------------------------------------------------
else 
echo "creating directory $HOME/.batchget" 
mkdir "$filedir"
echo "creating directory $HOME/.batchget/downloads"
mkdir "$dldir" 
#
exit 
fi
#------------------------------------------------------------------
if [ test -e / "$HOME"/.batchget/batchlog ] ; then
#
echo "reading batch file"
wget -nc -c -r -i "$HOME"/.batchget/batchlog.txt -p "$dldir"
echo "files in $HOME/.batchget/downloads"
exit 0
#------------------------------------------------------------------
else
#
echo "making file batchlog in $HOME/.batchget"
echo "#type the urls of the files that are to be downloaded" | cat > batchlog ; exit
mv   "$HOME"/batchlog "$HOME"/.batchget/batchlog
exit
fi
#------------------------------------------------------------------
[/B]

---

