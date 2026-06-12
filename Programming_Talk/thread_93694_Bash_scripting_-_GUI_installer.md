---
title: "Bash scripting - GUI installer"
date: 2005-11-22
forum: Programming Talk
---

### Post by Haegin on 2005-11-22
Hi, I am trying to write a bash script to install "any" program on linux (provided it uses deb, rpm or source atm). I am kinda picking it up as I go along and its just real basic at the moment but I am having problems. The code so far:
```

#!/bin/bash
## This script aims to enable users to install a program using a GUI interface as opposed to the command line.
## Unlike other similar offerings it attempts to install rpms, debs and source archives...

## Asks what package
pkgType=`zenity --list --title="Package Type" --text="What type of package are you installing?" --radiolist  --column="Check" --column="Package Name" FALSE Deb FALSE Rpm FALSE "Source(tar.bz)" FALSE "Source(tar.gz)"`
## Tells the terminal what package has been chosen.
echo $pkgType
if ["$pkgType" = "Rpm"]; then
echo $pkgType
else
echo "Not an rpm!"
fi

```
When I run it and select anything (including "Rpm") it echos the correct string but then when it compares it it decides that it isn't "Rpm" even if it is... Does anybody know why?

EDIT: I have now solved that problem using the case...esac conditional. My code now looks like this: 
```

#!/bin/bash
## This script aims to enable users to install a program using a GUI interface as opposed to the command line.
## Unlike other similar offerings it attempts to install rpms, debs and source archives...

## Asks what package
pkgType=`zenity --list --title="Package Type" --text="What type of package are you installing?" --radiolist  --column="Check" --column="Package Name" FALSE Deb FALSE Rpm FALSE "Source(tar.bz2)" FALSE "Source(tar.gz)"`
## Tells the terminal what package has been chosen.
#echo $pkgType
case $pkgType in
"Deb" ) echo "Package is a deb" ;;
"Rpm" ) echo "Package is an rpm" ;;
"Source(tar.bz2)" ) echo "Package is a bzipped source archive" ;;
"Source(tar.gz)" ) echo "Package is a gzipped source archive"
esac

```

As you can see - I added some stuff for the other types. This seems to work - If i get any more probs I will post here.

---

### Post by zootreeves on 2005-11-22
I am probably wrong but doesn't it have to be: (double ==)


if ["$pkgType" == "Rpm"]; then

---

### Post by Sheco on 2005-11-22
you have to have spaces after the [ and before the ]

if [ "$pkgType" == "Rpm" ]; then

---

### Post by Haegin on 2005-11-26
I have got a little further with my mini-script and have come across more problems. Just wondering if anybody could help. I have included the code at the end of this post. Currently I am having problems running the dpkg command - it always just posts a short lists of options then closes without installing the program.

```

#!/bin/bash
## This script aims to enable users to install a program using a GUI interface as opposed to the command line.
## Unlike other similar offerings it attempts to install rpms, debs and source archives...

## Asks what package
pkgType=`zenity --list --title="Package Type" --text="What type of package are you installing?" --radiolist  --column="Check" --column="Package Name" FALSE Deb FALSE Rpm FALSE "Source(tar.bz2)" FALSE "Source(tar.gz)"`

##What to do if its a deb
## Asks the path to the package
function debResult {
zenity --info --title="Package Path" --text="Click OK to select the package"
pkgPath=`zenity --file-selection --title="Package Path"`
echo $pkgPath
gksudo dpkg -i $pkgPath
zenity --info --title="Install Finished" --text="The installation has finished and the program is now installed."
}

##What to do if its an rpm
function rpmResult {
## Asks the path to the package
zenity --info --title="Package Path" --text="Click OK to select the package"
pkgPath=`zenity --file-selection --title="Package Path"`
rpmDescription=`zenity --entry --title="Description" --text="Enter a description of the program:"`
alien -i --description=$rpmDescription $pkgPath
}

##What to do if its a bzipped source archive
function bzipResult {
## Asks the path to the package
zenity --info --title="Package Directory" --text="Click OK to select the package location"
pkgDir=`zenity --file-selection --directory --title="Package Path"`
pkgPath=`zenity --entry --title="Package Filename" --text="Enter the package filename (e.g. example.tar.bz2)"`
#bzipDescription=`zenity --entry --title="Description" --text="Enter a description of the program:"`
cd $pkgDir
tar -xjf $pkgPath
make
gksudo checkinstall -y
}

## Conditional to do appropriate action depending on the package type
case $pkgType in
	"Deb" ) $(debResult) ;;
	"Rpm" ) $(rpmResult) ;;
	"Source(tar.bz2)" ) echo "Package is a bzipped source archive" ;;
	"Source(tar.gz)" ) echo "Package is a gzipped source archive" ;;
	* ) echo "Invalid selection!" & exit 0
esac

```

---

### Post by Haegin on 2005-11-28
Hmm... I still can't get this to work and I'm wondering if anybody can tell me why it won't work? It seems to be failing on the "gksudo dpkg -i $pkgPath" line but I can't see why - can you?

Thanks again,

---

### Post by Corvillus on 2005-11-28
gksudo only takes 1 parameter, it ignores the rest of the arguments. Use
```
gksudo "dpkg -i $pkgPath"
```
With those extra quotes there, it should work fine.

---

### Post by a-do-nis on 2009-05-29
I am not an developer, but an end user. I have been beging for exactly this feature since I began using linux some years ago. However, everyone even those employed by ubuntu and other distros keep telling me how easy it is to install from source. 
If it was so easy then why is this such an often requested feature and why is installation such a large volume complaint.
I apologize for rambling but this project of yours has me all exited. 
Like I said I am an end user so I can't offer programing support, but if there is any other way i can help this project reach completion let me know.

---

