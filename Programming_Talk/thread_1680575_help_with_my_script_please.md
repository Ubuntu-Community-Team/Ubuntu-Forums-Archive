---
title: "help with my script please"
date: 2011-02-02
forum: Programming Talk
---

### Post by JCarlin6 on 2011-02-02
In previous versions it worked but I downloaded them and re-ran them and they no longer work. They get to the images url and starts the download but it stops at 213 kb's EVERYTIME was there a update to python that I didnt see? Does this still work for anyone and if so what is your current python version??

```

#!/usr/bin/python

# Required modules
import urllib, random, xml.dom.minidom, re, os, glob, time;

class Wallbase:
	url         = 'http://wallbase.net/random/all/gteq/1366x768/0/110/60';

	urlResponse = None;
	urlRequest  = None;


	# Get HTML 
	def getHtml(self, url):
		# Get HTML
		self.urlRequest = urllib.URLopener().open(url);

		# Set HTML
		self.urlResponse = self.urlRequest.read();

		# Close URL request
		self.urlRequest.close();

		return self.urlResponse;



	# Get random wallpaper URL
	def getRandomWallpaperUrl(self, url):
		# Get HTML
		html = self.getHtml(url);

		# Create new DOM Document
		dom = xml.dom.minidom.parseString(html);

		# Get all images
		anchors = dom.getElementsByTagName('a');

		# No anchors found
		if anchors.length < 1:
			return;


		# New thumbs array
		thumbs = [];

		# Iterate over anchors
		for anchor in anchors:
			# Get attribute source
			href = anchor.getAttribute('href').encode('ascii', 'ignore');

			# Does it match thumb format?
			if re.search(r'wallpaper/\d+$', href):
				thumbs.append(href); # Append source to array

		# Random wallpaper url
		return random.choice(thumbs);



	# Set a random wallpaper
	def setRandomWallpaper(self):
		# Set wallpaper
		self.setWallpaper(self.getRandomWallpaperUrl(self.url));



	# Set a user specified wallpaper (pointless)
	def setWallpaper(self, url):
   		os.system('cp '+self.getWallpaper(url)+' /home/alpha/wallpapers/wallpaper');
		


	# Get random wallpaper
	def getWallpaper(self, url):
		print 'Getting Wallpaper: ' + url;

		# Get HTML
		html = self.getHtml(url);

		# Create new DOM Document
		dom = xml.dom.minidom.parseString(html);

		# Get all images
		imgs = dom.getElementsByTagName('img');

		# No images found
		if imgs.length < 1:
			return;


		# Iterate over images
		for img in imgs:
			# Get attribute source
			src = img.getAttribute('src').encode('ascii', 'ignore');

			# Does it match wallpaper format?
			if re.search(r'/wallpaper-\d+\.(?i)(?:gif|png|jpe?g)$', src):
				# Generate save path
				name = '/home/alpha/wallpapers' + src[src.rfind('/'):];

				# Does wallpaper already exist?
				if os.path.exists(name) == False:
					# Fetch image and save it
					urllib.urlretrieve(src, name);

				# Return wallpaper name
				return name;

# New Wallbase instance
wallbase = Wallbase();

# Set random Wallbase wallpaper
wallbase.setRandomWallpaper();
```

================================================

---

### Post by JCarlin6 on 2011-02-05
*bump* please =)

---

### Post by 3177 on 2011-02-05
weird, finished for me....

---

### Post by JCarlin6 on 2011-02-05
hmm. Are you completely updated?

---

### Post by 3177 on 2011-02-05
oh sorry, and its 3.1.3

---

### Post by 3177 on 2011-02-05
try 2.7.1 its still current

---

### Post by JCarlin6 on 2011-02-05
Thanks for the reply I could use all the help I can get right now

---

### Post by 3177 on 2011-02-05
just dawned on me. If you cant get your script to work. use the Ubuntu software center, im pretty sure its in there

---

### Post by JCarlin6 on 2011-02-05
I am not sure if its python or not actually. Its hard to figure out why it would only download 213 bytes without any errors to work off of 2.7.1 didnt work for me

---

### Post by JCarlin6 on 2011-02-07
Anyone else try this? Please need more people.... Anyone want to look at the code maybe its in there? ( Although I didnt see anything =/ )

---

### Post by JCarlin6 on 2011-02-14
Please I dont want my script to die and I do not understand what is wrong with it.

---

### Post by sdowney717 on 2011-02-20
how do I stop this script from running?
It has filled up my wallpaper folder with over 50,000 jpg and like you say, most are only 213bytes.

Ok, I think I found it called background.py
So I deleted it, perhaps now it wont fill up the wallpaper folder.

If you ever get the script to work again, you need to delete the wallpaper files and not let them load up to huge numbers of files.

---

### Post by snova on 2011-02-20
```

$ py tmp.py 
http://wallbase.net/wallpaper/288318
http://wallbase2.org/rozne/b52096a3ac0c586c419b1d91ec91ba82/wallpaper-288318.jpg

$ file wallpaper-288318.jpg 
wallpaper-288318.jpg: **HTML document text**

$ cat wallpaper-288318.jpg 
<html>
<head><title>503 Service Temporarily Unavailable</title></head>
<body bgcolor="white">
<center><h1>503 Service Temporarily Unavailable</h1></center>
<hr><center>nginx/0.8.54</center>
</body>
</html>

```

Your script works fine. It's lousy, but there's nothing wrong with it. For whatever reason, however, the image it attempts to download is instead this error page.

The website doesn't even work in Firefox, but does in Chrome (probably because of all the content blocking addons I use in FF). Chrome's developer console says it's downloading the same image that it should be, except if you try to go to it directly, it fails in both browsers. My conclusion is that they're doing something stupid with JavaScript.

---

