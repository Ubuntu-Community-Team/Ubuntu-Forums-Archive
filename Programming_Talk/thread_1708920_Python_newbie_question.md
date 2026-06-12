---
title: "Python newbie question"
date: 2011-03-17
forum: Programming Talk
---

### Post by AndyBoy_LV on 2011-03-17
Hi!

I usually code in PHP, but today i decided to take a break from it and write a small Python script :) It is the first time i code something in Python.

I have created a script that is being run by Audacious on every song change. Audacious passes filename and song title to it. Script then finds cover art for that song, that is stored locally on hard disk, and creates a notify-osd bubble with a new album cover and a song title.

I know that everything is working fine when i run this script from command line. But if ran by audacious, it stops on file reading-writing operation.

```
import hashlib
import sys
import os.path
import getpass
import time




user = getpass.getuser()



if len(sys.argv) > 2:
	


	#Notification status
	# 0 = Less than 11 seconds have passed since last notification
	# 1 = More than 11 seconds have passed since last notification
	status = 1



	#Cheks if configuration file exists. If not, creates it
	if os.path.isfile('config.txt') == False:
		os.system('touch config.txt')
		


	#Gets last notification time
	config = open('config.txt', 'r')
	lastNotification = config.readline()

	
	
	#If lastNotification is empty, sets it to 0
	if len(lastNotification) == 0:
		lastNotification = 0
	

	lastNotification = float(lastNotification)
	config.close()

	
	#Gets current time	
	currentTime = time.time()


	#If previous notification has already disappeared
	#	puts a new one in the file
	if currentTime - lastNotification > 11:

		#Clears config file and puts new notification time
		config = open('config.txt', 'w')
		config.write(str(currentTime))
		config.close()
		status = 1




	#If more than 11 seconds have passed since last notification, shows  a new one
	if status == 1:
	
		title = sys.argv[2]
		filename = sys.argv[1]

		#os.system('notify-send "Cover exists"')

		#Gets file md5 hexdigest hash	
		cover = hashlib.md5(sys.argv[1]).hexdigest()
	
		#Finds hashed file in .thumbnails directory
		cover = '/home/' + user + '/.thumbnails/normal/' + cover + '.png'
	
	
		#If thumbnail exists, sends notification
		if os.path.isfile(cover):
			os.system('notify-send -i ' + cover + ' "Audacious" "' + title + '"')
	
		#Else - looks for it in the directory of the file
		else:
		
			folderArt = 0

			#Gets music file`s directory from Audacious
			filename = filename.replace("file://", "")
			filename = filename.replace("%20", "\ ")
			filename = filename.replace(os.path.basename(filename), "")
	
			#Gets all files in a directory
			dirList=os.listdir(filename)
	
			#Searches for an image file in this directory
			for fname in dirList:
			    if os.path.splitext(fname)[1] == ".jpeg" or os.path.splitext(fname)[1] == ".jpg" or os.path.splitext(fname)[1] == ".png":
		
				#Sends notification message
				os.system('notify-send -i "' + filename  + fname + '" "Audacious" "' + title + '"')
				folderArt = 1
				break
		
			#If there are no images in that directory, sends default image
			if folderArt == 0:
				os.system('notify-send -i audacious "Audacious" "' + title + '"')



	
```

I need to store last notification time in an external configuration file (config.txt), because of notify-osd bug, which does not allow to clear current notification. 

When i run this code from Terminal, it works as it is supposed to. When Audacious runs it, it stops on ```
	config = open('config.txt', 'r')
```Is it some permission problem? How can i overcome it?

Any help would be appreciated.

---

### Post by Arndt on 2011-03-17
> **AndyBoy_LV said:**
> Hi!

I usually code in PHP, but today i decided to take a break from it and write a small Python script :) It is the first time i code something in Python.

I have created a script that is being run by Audacious on every song change. Audacious passes filename and song title to it. Script then finds cover art for that song, that is stored locally on hard disk, and creates a notify-osd bubble with a new album cover and a song title.

I know that everything is working fine when i run this script from command line. But if ran by audacious, it stops on file reading-writing operation.

```
import hashlib
import sys
import os.path
import getpass
import time




user = getpass.getuser()



if len(sys.argv) > 2:
	


	#Notification status
	# 0 = Less than 11 seconds have passed since last notification
	# 1 = More than 11 seconds have passed since last notification
	status = 1



	#Cheks if configuration file exists. If not, creates it
	if os.path.isfile('config.txt') == False:
		os.system('touch config.txt')
		


	#Gets last notification time
	config = open('config.txt', 'r')
	lastNotification = config.readline()

	
	
	#If lastNotification is empty, sets it to 0
	if len(lastNotification) == 0:
		lastNotification = 0
	

	lastNotification = float(lastNotification)
	config.close()

	
	#Gets current time	
	currentTime = time.time()


	#If previous notification has already disappeared
	#	puts a new one in the file
	if currentTime - lastNotification > 11:

		#Clears config file and puts new notification time
		config = open('config.txt', 'w')
		config.write(str(currentTime))
		config.close()
		status = 1




	#If more than 11 seconds have passed since last notification, shows  a new one
	if status == 1:
	
		title = sys.argv[2]
		filename = sys.argv[1]

		#os.system('notify-send "Cover exists"')

		#Gets file md5 hexdigest hash	
		cover = hashlib.md5(sys.argv[1]).hexdigest()
	
		#Finds hashed file in .thumbnails directory
		cover = '/home/' + user + '/.thumbnails/normal/' + cover + '.png'
	
	
		#If thumbnail exists, sends notification
		if os.path.isfile(cover):
			os.system('notify-send -i ' + cover + ' "Audacious" "' + title + '"')
	
		#Else - looks for it in the directory of the file
		else:
		
			folderArt = 0

			#Gets music file`s directory from Audacious
			filename = filename.replace("file://", "")
			filename = filename.replace("%20", "\ ")
			filename = filename.replace(os.path.basename(filename), "")
	
			#Gets all files in a directory
			dirList=os.listdir(filename)
	
			#Searches for an image file in this directory
			for fname in dirList:
			    if os.path.splitext(fname)[1] == ".jpeg" or os.path.splitext(fname)[1] == ".jpg" or os.path.splitext(fname)[1] == ".png":
		
				#Sends notification message
				os.system('notify-send -i "' + filename  + fname + '" "Audacious" "' + title + '"')
				folderArt = 1
				break
		
			#If there are no images in that directory, sends default image
			if folderArt == 0:
				os.system('notify-send -i audacious "Audacious" "' + title + '"')



	
```

I need to store last notification time in an external configuration file (config.txt), because of notify-osd bug, which does not allow to clear current notification. 

When i run this code from Terminal, it works as it is supposed to. When Audacious runs it, it stops on ```
	config = open('config.txt', 'r')
```Is it some permission problem? How can i overcome it?

Any help would be appreciated.

Is it certain that the current directory is the one where config.txt is located?

---

### Post by AndyBoy_LV on 2011-03-17
> **Arndt said:**
> Is it certain that the current directory is the one where config.txt is located?


Thank you for your reply!

Yo are right, i should have inserted absolute path. Silly me.

Now everything seems to work fine.

---

