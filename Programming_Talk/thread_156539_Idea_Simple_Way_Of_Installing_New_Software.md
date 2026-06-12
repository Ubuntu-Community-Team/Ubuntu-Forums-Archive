---
title: "Idea: Simple Way Of Installing New Software"
date: 2006-04-07
forum: Programming Talk
---

### Post by Mucki on 2006-04-07
Hi,

this is my first post here :)

I had an idea that might make installing third party software or just additional software/codecs etc easier, but I am not sure if it's a good idea and worth it.

I want to use Opera as example:
Currently you go to their website, download the .deb and install it with dpkg, but then you have to check for updates manually (I know that Opera does check automatically ;)), or you add their repository to your sources.list, which is still a bit inconvenient for the very basic user.

My idea is to create a simple XML file which looks something like this:
```

	<dwi>
		<distribution="ubuntu" version="dapper">
			<rep type="deb" uri="http://myrep.com" distribution="dapper" sections="main restricted universe multiverse" />
			or
			<rep>deb http://myrep.com dapper main restricted universe multiverse</rep>
			<package name="firefox">Description here</package>
			<package name="thunderbird">Description here</package>
		</distribution>
		<distribution="debian" version="sid">
			<rep type="deb" uri="http://myrep.com" distribution="sid" sections="main restricted universe multiverse" />
			or
			<rep>deb http://myrep.com sid main restricted universe multiverse</rep>
			<package name="firefox">Description here</package>
			<package name="thunderbird">Description here</package>
		</distribution>
	</dwi>

```

When you click that file in the browser it will open with the associated program, just like a .torrent would open ktorrent for example.
Then the program would check whether your distribution/version is in that file, check if the listed repositories are already in the sources.list, if not it will ask if you are sure that you want to trust that source and then add it. And finally it will ask you if you are sure that you want to install the listed programs, e.g. firefox and thunderbird as in the example file above.

I hope it's clear that packages and repositories in the XML file are both optional.
So you could also use this:
```

<dwi>
	<distribution="ubuntu" version="breezy">
		<rep>deb http://kubuntu.org/packages/kde352 breezy main</rep>
	</distribution>
	<upgrade value="true" />
</dwi>

```
this would add the KDE 3.5.2 repository, [COLOR="red"]only[/COLOR] if you're using breezy, to your sources.list and then call apt-get update & apt-get upgrade, thus updating your currently installed KDE to the latest version with just a few clicks.

Another advantage would be in all the wikis, e.g. instead of
> 
Other Non-Free Formats
The Ubuntu and Kubuntu media players can support a wide variety of non-free formats. If it is legal for you to play these formats, just  enable the universe and multiverse repositories and install the necessary packages with your favorite package manager. Alternatively, you can type in a terminal: 
```
sudo apt-get install  gstreamer0.8-plugins  gstreamer0.8-plugins-multiverse  gstreamer0.8-ffmpeg
```
  
or, if you are using Ubuntu 6.06 (Dapper Drake): 
```
sudo apt-get install gstreamer0.10-ffmpeg gstreamer0.10-gl gstreamer0.10-plugins-base gstreamer0.10-plugins-good gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse libxine-extracodecs ffmpeg lame faad sox mjpegtools libxine-main1
```

use
```

<dwi>
	<distribution="ubuntu" version="breezy">
		<package name="gstreamer0.8-plugins"></package>
		<package name="gstreamer0.8-plugins-multiverse"></package>
		<package name="gstreamer0.8-ffmpeg"></package>
	</distribution>
	<distribution="ubuntu" version="dapper">
		<package name="gstreamer0.10-ffmpeg"></package>
		<package name="gstreamer0.10-gl"></package>
		<package name="gstreamer0.10-plugins-base"></package>
		<...>
	</distribution>
<dwi>

```

I know programs like automatix do a great job doing automatic installations, and this idea isn't supposed to replace them, but to extend the possibilities.

I am aware about the possible security risks, that non careful users could just click any file without thinking and thus adding possible malicious repositories. :???: 

So what do you guys think of this?

---

### Post by 3rdalbum on 2006-04-08
I like the idea. Would there be a way to include the system into RPM-based distros?

---

### Post by Mucki on 2006-04-09
I don't really know RPM, but yum uses repositories too if I'm not mistaken. So yes, that could be realised, too.

---

