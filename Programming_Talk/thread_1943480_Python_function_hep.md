---
title: "Python function hep?"
date: 2012-03-19
forum: Programming Talk
---

### Post by akernan on 2012-03-19
I'm starting with python, need some help.  This error is confusing.  I got the original python script off the crunchang forums.  It worked fine but copied files and I wanted to symlink and made a few other changes.  I was getting an error about file existing when the symlink was created.  I decided to write a function to delete the files before the symlink.  I use an if statement too control when files are deleted.  The problem is the if statement works in one function but not another.  The files get created then deleted shortly afterwards.  Here's the function in question and a similar one that is working.

**Problem function..**
```
def check_artist_art():
    if os.path.exists("/tmp/artistinfo") and open("/tmp/artistinfo").read() != title:
        if os.path.exists(home + "/.artist"):
            os.remove(home + "/.artist")
        if os.path.exists("/tmp/artistinfo"):
            os.remove("/tmp/artistinfo")
            print artist
        return False
    elif os.path.exists("/tmp/artistinfo") and open("/tmp/artistinfo").read() == artist:
        return False
    return True

```

**Function that works correctly...**
```

def check_album():
    if os.path.exists("/tmp/albuminfo") and open("/tmp/albuminfo").read() != album:
        if os.path.exists(home + "/.album"):
            os.remove(home + "/.album")
        if os.path.exists("/tmp/albuminfo"):
            os.remove("/tmp/albuminfo")
        return False
    elif os.path.exists("/tmp/trackinfo") and open("/tmp/trackinfo").read() == artist + album:
        return False
    return True

```

**Here's the full python script..**
```

#!/usr/bin/python
#Start from albumart-f.py

import commands
from optparse import OptionParser

#retrieve track info from player
def get_info():
    check_running = commands.getoutput("ps aux")
    check_running = check_running.split("\n")
    for line in check_running:
        if "mocp" in line:
            return commands.getoutput("mocp -Q %artist"),commands.getoutput("mocp -Q %album"),commands.getoutput("mocp -Q %song"),commands.getoutput("mocp -Q %file")
    return "","","",""

#resize image
def size_image(width, height, path):
    image = Image.open(path)
    image = image.resize((width, height))
    image.save(path, "png")

#add reflection to image
def reflect(width, height, path):
    image = Image.open(path)
    flipped_image = image.transpose(Image.FLIP_TOP_BOTTOM)
    final_image = Image.new('RGBA', (width, (height * 2) + 1) , (0, 0, 0, 0))
    gradient = Image.new('L', (1,255))
    for y in range(255, 0, -1):
        if y < 128:
            gradient.putpixel((0,y),255 - (y * 2))
        else:
            gradient.putpixel((0,255-y),0)
    alpha = gradient.resize(flipped_image.size)
    flipped_image.putalpha(alpha)
    final_image.paste(image, (0, 0))
    final_image.paste(flipped_image, (0, height + 1))
    final_image.save(path, "png")

def check_album():
    if os.path.exists("/tmp/albuminfo") and open("/tmp/albuminfo").read() != album:
        if os.path.exists(home + "/.album"):
            os.remove(home + "/.album")
        if os.path.exists("/tmp/albuminfo"):
            os.remove("/tmp/albuminfo")
        return False
    elif os.path.exists("/tmp/trackinfo") and open("/tmp/trackinfo").read() == artist + album:
        return False
    return True

#fetch album
def get_album():
    if not os.path.exists(musicdir + "/cover.png"):
        api_album = api.get_album(album, artist)
        if api_album.image["extralarge"]:
            urllib.urlretrieve(api_album.image["extralarge"], musicdir + "/cover.png")
        elif api_album.image["large"]:
            urllib.urlretrieve(api_album.image["large"], musicdir + "/cover.png")
        elif api_album.image["medium"]:
            urllib.urlretrieve(api_album.image["medium"], musicdir + "/cover.png")
        elif api_album.image["small"]:
            urllib.urlretrieve(api_album.image["small"], musicdir + "/cover.png")
        else:
            commands.getoutput("cp %s %s" % (home + "/Pictures/Nocover.png", musicdir + "/cover.png"))
    open("/tmp/trackinfo","w").write(artist + album)
    open("/tmp/albuminfo","w").write(album)
    #commands.getoutput("cp '%s' '%s'" % ("%s/cover.png" % (musicdir), home + "/.album"))
    os.symlink(musicdir + "/cover.png", home + "/.album")
    size_image(width, height, home + album_path)
    if options.reflect:
        reflect(width, height, home + album_path)

def check_artist_art():
    if os.path.exists("/tmp/artistinfo") and open("/tmp/artistinfo").read() != title:
        if os.path.exists(home + "/.artist"):
            os.remove(home + "/.artist")
        if os.path.exists("/tmp/artistinfo"):
            os.remove("/tmp/artistinfo")
            print artist
        return False
    elif os.path.exists("/tmp/artistinfo") and open("/tmp/artistinfo").read() == artist:
        return False
    return True

#fetch artist art
def get_artist_art():
    if not os.path.exists(musicdir + "/" + artist + ".png"):
        api_artist = api.get_artist(artist)
        if api_artist.image["extralarge"]:
            urllib.urlretrieve(api_artist.image["extralarge"], musicdir + "/" + artist + ".png")
        elif api_artist.image["large"]:
            urllib.urlretrieve(api_artist.image["large"], musicdir + "/" + artist + ".png")
        elif api_artist.image["medium"]:
            urllib.urlretrieve(api_artist.image["medium"], musicdir + "/" + artist + ".png")
        elif api_artist.image["small"]:
            urllib.urlretrieve(api_artist.image["small"], musicdir + "/" + artist + ".png")
        else:
            commands.getoutput("cp %s %s" % (home + "/Pictures/Nocover.png", musicdir + "/" + artist + ".png"))
    open("/tmp/artistinfo","w").write(artist)
    #commands.getoutput("cp '%s' '%s'" % ("%s/%s.png" % (musicdir, artist), home + "/.artist"))
    os.symlink(musicdir + "/" + artist + ".png", home + "/.artist")
    size_image(width, height, home + artist_path)
    if options.reflect:
        reflect(width, height, home + artist_path)

def check_similar():
    if title == "":
        if os.path.exists(home + "/.similar"):
            os.remove(home + "/.similar")
        if os.path.exists("/tmp/titleinfo"):
            os.remove("/tmp/titleinfo")
        return False
    if os.path.exists("/tmp/titleinfo") and open("/tmp/titleinfo").read() == title:
        return False
    return True

def get_similar():
    api_artist = api.get_artist(artist)
    out = ""
    for item in api_artist.get_similar(limit=5):
        out = out + item.name + "\n"
    open(home + "/.similar", "w").write(out)

#set up command line options
parser = OptionParser()
parser.add_option("-s", "--size", dest="size", default="80x80", help="image size")
parser.add_option("-r", "--reflect", action="store_true", dest="reflect", default=False, help="image reflection")
parser.add_option("-a", "--artist-art", action="store_true", dest="artist_art", default=False, help="artist image")
parser.add_option("-n", "--net", action="store_true", dest="internet_art", default=False, help="internet image")
parser.add_option("--artist", action="store_true", dest="return_artist", default=False, help="artist")
parser.add_option("--album", action="store_true", dest="return_album", default=False, help="album")
parser.add_option("--title", action="store_true", dest="return_title", default=False, help="title")
parser.add_option("--similar", action="store_true", dest="similar_artists", default=False, help="similar artists")
(options, args) = parser.parse_args()

#check if size is valid
try:
    width,height = options.size.split("x")
    width = int(width)
    height = int(height)
except:
    parser.error("please specify size in WIDTHxHEIGHT format")

artist, album, title, musicfile = get_info()

#return artis, album, or title
if options.return_artist:
    print artist
    raise SystemExit()
if options.return_album:
    print album
    raise SystemExit()
if options.return_title:
    print title
    raise SystemExit()


import Image, os
#set up variables
home = os.getenv("HOME")
album_path = "/.album"
artist_path = "/.artist"
musicdir = commands.getoutput('dirname "' + musicfile + '"')
api_key = "5227173234d678f9eb9d415a1ff04489"

if check_artist_art() or check_album() or check_similar():
    import urllib, lastfm, re
    api = lastfm.Api(api_key)

if options.similar_artists and check_similar():
    get_similar()
    if os.path.exists(home + "/.similar"):
        print open(home + "/.similar").read()
    raise SystemExit()

if options.artist_art and check_artist_art():
    get_artist_art()

if check_album():
    get_album()

```

---

### Post by Arndt on 2012-03-20
With code like this:

```
   open("/tmp/artistinfo","w").write(artist)
```

it's not certain that what is written appears on disk immediately. You should close the file too.

What is actually in the relevant files at the point where their contents is read?

---

### Post by akernan on 2012-03-20
> **Arndt said:**
> With code like this:

```
   open("/tmp/artistinfo","w").write(artist)
```

it's not certain that what is written appears on disk immediately. You should close the file too.

What is actually in the relevant files at the point where their contents is read?

I'll try closing them.  The relevant files should have song info when they're read.

Maybe put a sleep statement after the write?

---

### Post by cgroza on 2012-03-20
> **akernan said:**
> I'll try closing them.  The relevant files should have song info when they're read.

Maybe put a sleep statement after the write?
Putting a sleep statement after the write is not necessary. You can call the flush() method to force the file object write the contents immediately. This should not be needed either if you are calling close() later because this method flushes the buffers before closing the file.

And consider using os.path.join to construct the paths.

---

### Post by akernan on 2012-03-20
I got angry and took another good, hard, logic look.  Then I found the problem, a simple problem that was causing a **BIG** headache.  I was using the wrong varible in a test statement.  :(

Works great now that I use the variable.

---

