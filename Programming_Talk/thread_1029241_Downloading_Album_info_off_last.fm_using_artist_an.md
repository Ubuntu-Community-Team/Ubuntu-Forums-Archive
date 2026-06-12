---
title: "Downloading Album info off last.fm using artist and title name?"
date: 2009-01-03
forum: Programming Talk
---

### Post by lswest on 2009-01-03
Okay, so I know a bit about bash scripting (pretty much just what I use regularly to make life easier), and I've been going through my music collection, and I realized there are quite a few songs in there that are missing some info from ID3 tags (album, track, year and genre mainly because I was too lazy to enter those back when my computer wouldn't recognize the info off the CD or download it off the 'net itself a few years ago).  About the genre, I found a ruby script that uses the most popular tag from last.fm to fill in the info, but it can't be re-worked for the others, and isn't the most accurate way to do it.

My question is this:
Do you guys think it's possible to write a bash script to fetch the rest of the info off the 'net using the already present artist and title information in the id3 tag, and automatically append it to the tags?

The other option is to do it by hand...and that'd be a pain.

If it's not possible using bash, any suggestions in python, perl, or any other programming language would be fine too.

Thanks in advance for any suggestions you have,
Lswest

---

### Post by .Maleficus. on 2009-01-03
That's definitely possible.  I actually wrote a Python script to fetch recommended artists from my last.fm account based on the artists I already have in my library - it was actually really easy.  Sign up for a key to use the last.fm API (it's on their website) and then Google 'pylast', the Python implementation of the last.fm API.

---

### Post by lswest on 2009-01-03
Great, I'll have a look into it, thanks.

Okay, well I have it set up, but I believe I need some help writing the python script to read in (recursively) the directory tree of my Music/ folder, I can probably take it from there, but I'm not able to get it to access more than one layer below the root path I specify.  I imagine I have to put in a os.listdir(path) check, and then join the listed directories to that and continue like that?

something like:
```
for dirs in os.walk(path):
	#check to see if there are directories in that folder, and if so, add them to the path
	if(os.listdir(path)):
		print glob.glob(os.path.join(path, '*.mp3'))
		path=os.path.join(path, os.path.split(dirs))
	else:
		#Otherwise, just print the files in the folder
		print glob.glob(os.path.join(path, '*.mp3'))
```
I realize the code above doesn't work, but I put it there to try to illustrate what I mean, I'm trying to figure out where the problem is (python isn't my strongest language).

---

