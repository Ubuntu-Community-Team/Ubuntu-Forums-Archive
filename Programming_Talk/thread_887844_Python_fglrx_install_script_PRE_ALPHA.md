---
title: "Python fglrx install script PRE ALPHA"
date: 2008-08-12
forum: Programming Talk
---

### Post by soxs on 2008-08-12
I wrote a tiny python script, allowing me to install the latest (atm fglrx 8.7) back to 8.6 (becuase that's the last one having the option --buildandinstall).

It will not clean up any old drivers like 8.42.x or any older, simply becuase I don#t know about where hey installed all their stuff (So it will work for Radeon 9500 and newer).

Another thing it won't do is fixing the /etc/X11/xorg.conf (yet, though I have no big pull to do it by hand) or passing it to the restriced modules (Though this never was required with any flgrx drivers for me, the hell knows why)

I would like to hear some devs inentions of that script, what can be improved in my style of coding and so on.
NOTE: THIS IS NOT INTENDED TO BE 100% CORRECT WORKING (YET!).

I am going to regulalry update this thread, I will make bugfixes and updates for new driver releases and so on...

Note: I know about envy/envng and it's frontends, but I don't like the way it works... though I used it some time ago, but for me it was like playing russian roulette: 3D or blackscreen

So here we go
```
#!/usr/bin/env python
#-*- coding: utf-8 -*-
	 
# This program is free software; you can redistribute it and/or modify
# it under the terms of the GNU General Public License as published by
# the Free Software Foundation; either version 3, or (at your option)
# any later version.
#
# This program is distributed in the hope that it will be useful,
# but WITHOUT ANY WARRANTY; without even the implied warranty of
# MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE. See the
# GNU General Public License for more details.
#
# You should have received a copy of the GNU General Public License
# along with this program; if not, write to the Free Software
# Foundation, Inc., 675 Mass Ave, Cambridge, MA 02139, USA.

# VERSEION 0x0000002
# AUTHOR BERNHARD SCHUSTER aka soxs or sox060389
# C 2008 // WELL IS THAT REQUIRED FOR GPLED CODE?

def CON(string,T="E"):
	T=T[:1].upper()
	COL_ERROR ="\033[31m"
	COL_QUEST ="\033[34m"
	COL_INFO  ="\033[32m"
	COL_REMOVE="\033[0m"
	if "E" in T:
		string=COL_ERROR+string+COL_REMOVE
	elif "I" in T:
		string=COL_INFO+string+COL_REMOVE
	elif "Q" in T:
		string=COL_QUEST+string+COL_REMOVE
	return string

class Download(object):

	def __init__(self,url,target):
		self.current=0
		self.__last=-1
		self.url=url
		self.target=target

	def percent(self,blocks,blocksize,size):
		self.current=blocksize*blocks*100/size
		if self.current>100:
			self.current=100
		if self.current != self.__last :
			self.__last=self.current
			print "%d%%" % self.current
	def getitdown(self):
		print CON("\n\n\nStarting download...\n[This may take some time, depending on your net speed]","I")
		#print self.url + " ->" + self.target
		try:
			urllib.urlretrieve(self.url,self.target,self.percent)
		except IOError:
			print CON("IOERROR!!!")
			return -1
		finally:
			self.__del__
		return 0
	
	def __del__(self):
		print CON("Download Completed.\n\n","I")



def Download_FGLRX(url,target):
	D=Download(url,target)
	return D.getitdown()


def CreateSubfolder(path="",sub="fglrx_debs",change=True):
	if path=="":
		path=os.getcwd()
	path=path+"/"+sub
	try:
		os.system("sudo mkdir -p -m 755 "+path)
		#os.mkdir(path)
	except:
		print CON("Error: Dir couldn't be created:"+path+"\nAborting..[1]","E")
		sys.exit(1)
	path=os.path.realpath(path)
	if change:
		os.chdir(path)	
	return path


def CopyInstallerToSubfolder(i_path,sub):
	print i_path
	sub=CreateSubfolder(os.path.split(i_path)[0],sub,True)
	i_name=os.path.split(i_path)[1]
	i_copy=sub+"/"+i_name
	os.system("sudo cp -vf "+i_path+" "+i_copy+"; sudo chmod -Rvf "+sub+"/*")
	return i_copy


def CopyInstallerToSubfolderDL(i_path,sub,url,download,i_version):
	if url=="":
		i_version=i_version.replace(" ","-").replace(".","-").replace("_","-") #get rid of any alternate spacing chars
		V=["8-7","8-6"]
		if i_version in V:
			i_name="ati-driver-installer-"+i_version+"-x86.x86_64.run"
			url="https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/"+i_name
		else:
			print CON("Error: Unhandled driver version ["+i_version.replace("-"," ")+"] \n Aborting..[7]","E")
			sys.exit(7)


	i_path=download+"/"+i_name
	print i_path
	if 0!=Download_FGLRX(url,i_path) :
		print CON("Error: Download unexpectitly exited, try another url or download it by hand and use the -a option.\nAborting..[5]","E")
		sys.exit(5)
	

	 ### donwload is not the correct name
	return CopyInstallerToSubfolder(i_path,sub), i_path








def ClearRefuges():
	Q=[8.512,8.501]
	for version in Q:
		os.system("sudo dkms uninstall -m fglrx -v "+str(version)+">/dev/null")
	os.system("sudo rm -Rvf /var/lib/dkms/fglrx")
	os.system("sudo rm -vf /lib/modules/$(uname -r)/updates/dkms/fglrx.ko")
#	os.remove("/lib/modules/2.6.*-*-generic/updates/dkms/fglrx.ko")
	print CONV("Brute Force Clear succsessfully done","I")

#############################################################################
#############################################################################

		###### ########  ####   #####   ########
		###### ######## ######  ######  ########
		##        ##    ##  ##  ##  ##     ##
		######    ##    ######  #####      ##
		######    ##    ######  #####      ##
		    ##    ##    ##  ##  ##  ##     ##
		######    ##    ##  ##  ##  ##     ##
		######    ##    ##  ##  ##  ##     ##

#############################################################################
#############################################################################

#!/usr/bin/env python
import os
import sys
import shutil
import urllib
from optparse import OptionParser

parser = OptionParser("install_fglrx.py [options]")
parser.add_option("-i", "--installbuilddep", action="store_true", dest="bfc", default=False, help="Install common required tools to make the installer work.")
parser.add_option("-b", "--bruteforceclear", action="store_true", dest="ix", default=False, help="If you messed up everything, this will remove any garbage  fglrx created (in theory) aswell as any fglrx kernel modules and exit then.\n Note: This won't purge envy installed drivers, or only partly, so first remove anything possible with envyng before attempting to use switch -b. ")
parser.add_option("-a", "--alternate", dest="alt", default="", help="Give an alternate installer instead of the download option.")
parser.add_option("-d", "--download", dest="download", default="~/Desktop", help="Give an alternate location as dl target for the fglrx driver")
parser.add_option("-u", "--url", dest="url", default="", help="Give an alternate url from where to dl the fglrx driver")
parser.add_option("-v", "--version", dest="iversion", default="8.7", help="Fglrx driver version, default is 8.7, atm 8.6 is the only alternative to 8.7, older versions suck hard and lack a required install routine.")
parser.add_option("-r", "--release", dest="release", default="hardy", help="Give Your ubuntu version e.g. gutsy hardy inteprid (the only ones which I recommend to use, default is hardy) or its pending version number 7.10 8.04 8.10, you may aswell pass anything that is known by the ati driver.")
option, args = parser.parse_args()

release=option.release.lower()

sub="fglrx_deb_pkgs"



## is this required or does the ati installer do its ob properly
if option.bfc:
	ClearRefuges()
	sys.exit(0)

if option.ix:
	print CON("Installing dependencies ...","I")
	os.system("sudo apt-get update; sudo apt-get install build-essential fakeroot dh-make debhelper debconf libstdc++5 dkms linux-headers-$(uname -r)")


if i_path!="":
	if os.path.exists(i_path):
		i_path=os.path.realpath(os.path.abspath(option.alt))
	else:
		print CON("Error: Option -a path is invalid and/or not existant.\n Aborting..[2]","E")
		sys.exit(2)
	if os.path.isfile(i_path):
		i_copy=CopyInstallerToSubfolder(i_path,sub)
	else:
		print CON("Error: Option -a does not point to a file.\n Aborting..[2]","E")
		sys.exit(2)
else:
	download = option.download
	if not os.path.isdir(download):
		download=os.path.realpath("./")
		print CON("Error: You gave an incorrect download directory. Taking <<"+download + ">> instead","E")
	i_copy,i_path=CopyInstallerToSubfolderDL("",sub,option.url,download,option.iversion)










allowed=["inteprid","8.10","hardy","8.04","gutsy","7.10"]
warning=["inteprid","8.10"]
if release in warning:
	skip = raw_input(CON("This driver won't support "+ build +"'s standard xserver/xorg version. Unless you already downgraded your xorg, skip.\nSkip [Y/n]","Q"))
	if skip.lower()!="n":
		print CON("Aborting..[3]","E")
		sys.exit(3)

if release in allowed:
	release="Ubuntu/"+release
else:
	skip = raw_input(CON("Your build coulnd't be referenced to neither hardy nor gutsy nor inteprid. This will be directly passed to the fglrx install routine.\nIf you are not sure what to write here, consider skipping here and run << sudo sh " + i_copy + " --listpkg >> from console which will show you any sensible options.\nSkip? [Y/n]","Q"))
	if skip.lower()!="n":
		print CON("Aborting..[4]","E")
		sys.exit(4)


try:
	
	os.system("sudo ln -sfv /usr/lib/libGL.so.1.2 /usr/lib/libGL.so.1") # required to make 8.6 compile
except:
	print CON("Error. Linking failed. in case you're going tonstall 8.6, it will fail.\nAborting..[6]","E")
	sys.exit(6)

#print CON(i_copy,"I")
#print CON(release,"I")
try:
	print CON("Executing proprietary fglrx @ "+i_copy+" installer... for "+release,"E")
	os.system("sudo "+i_copy+" --buildandinstallpkg "+release)
except:
	print CON( "Error. Installer unexpectly exited.\nAborting..[7]","E")
	sys.exit(7)
finally:
	os.remove(i_copy)


try:
	os.system("sudo dpkg -i *.deb")
except:
	print CON("Error. Packages couldn't be installed.\nAborting..[8]","E")
	sys.exit(8)


sys.exit(0)

### xorg.conf parsing..???
### still lacking it :-S
```


12Aug2008_INITIAL 0x0000001
[COLOR="Green"]12Aug2008_UPDATE 0x0000002[/COLOR]: --installdependencies and --bruteforceclear set the sam var which would have resulted in installing dependencies while going to bruteforceclear any refuges
[COLOR="Red"]12Aug2008_UPDATE 0x0000003[/COLOR]: Will work with any kernel from now, not only generic

---

### Post by Reiger on 2008-08-12
That I'm somewhat confused seeing as all this is available through the Ubunutu repositories... In nice .deb packages?

```

aptitude install fglrx-control

```

Ought to do it?

---

### Post by soxs on 2008-08-12
> **Reiger said:**
> That I'm somewhat confused seeing as all this is available through the Ubunutu repositories... In nice .deb packages?

```

aptitude install fglrx-control

```

Ought to do it?

Well, you won't get the bleeding edge fglrx drivers for the latest GPUs.
Though, fglrx-control is just the frontend for the actual driver and for itself useless, if it hadny't the actual driver (I think 8.4 8.5 or 8.6 as dependencies which is in the ubuntu repositories)

---

### Post by Reiger on 2008-08-12
Yeah but it depends on the driver. ;)

---

### Post by soxs on 2008-08-12
> **Reiger said:**
> Yeah but it depends on the driver. ;)

But not the bleeding edge one, that's the actual reason this script exists...

---

### Post by soxs on 2009-04-04
[B]DON'T USE THIS SCRIPT ANYMORE!!! 

It's outdated, and I am running fedora right now and I am goging to stick with that in the forseeable future.
[/B]

---

