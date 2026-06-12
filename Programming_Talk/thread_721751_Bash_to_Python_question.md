---
title: "Bash to Python question"
date: 2008-03-11
forum: Programming Talk
---

### Post by bvmou on 2008-03-11
Does anyone know how I might express the following shell command in Python?
```

find ~/podcasts/current -mindepth 2 -mtime '+`a`+' -exec mv {} ~/podcasts/old \;
```

...where 'a' is a user-input number of days worth of podcasts to keep on a mass storage device.

I  am using os.system('the bash command') but would like to make it more portable.

---

### Post by Can+~ on 2008-03-11
Let me understand. Your bash script finds everything in the new podcasts folder (why don't use an ls then?), and moves the ones that are older than <user_input> to the old podcast folder?

Well, I'm not 100% skilled in python, but let's break the problem (and googling):

Getting the files in the podcast folders : os.lisdir(path) [COLOR="Lime"]check[/COLOR]
Getting the creation time : Actually, I had to google this one, all references I find say that "int_time = os.stat(path)[stat.ST_CTIME]" for that. [COLOR="Lime"]check[/COLOR]
Moving the files : [shutil library (link here)](http://docs.python.org/lib/module-shutil.html) [COLOR="Lime"]check[/COLOR]

References:
[http://www.thescripts.com/forum/thread732946.html](http://www.thescripts.com/forum/thread732946.html)

---

### Post by bvmou on 2008-03-11
Thanks Can,

I am using shutil and os.listdir, etc, for the python equivalent of 

```
cp -ru /source /destination
```

The idea is to add some time and access info to manage space on the storage device.  I could use os.system('ls') [or os.system('any bash command') but I would like to be able to share the results with my old man, who has the same phone and Windows.

os.stat is definitely what I was missing for the atime mtime ctime bits, thanks again.

If anyone has a knockout python 1-4 liner for that first shell command, would love to know it.

---

### Post by ghostdog74 on 2008-03-11
you can use os.walk(). for mindepth , you have to some how get a count of the depth level from the output of os.walk. For mtime, you can either use os.stat or getmtime() method. if you find it a hassle to recode everything in Python, you can use things like cygwin ( or[ GNU find for Windows ]("http://gnuwin32.sourceforge.net/packages/findutils.htm")if porting to Windows)then only minimal changes need to be done on your one line find command.

---

### Post by slavik on 2008-03-11
```

cmd = "find ~/podcasts/current -mindepth 2 -mtime '+" + ARGV[1] + "+' -exec mv {} ~/podcasts/old"
os.system(cmd)

```

I dunno what has to go instead of ARGV[1]

but I do have a question of why you want this in Python, is there something else you want to do or just allow the user to put in an argument?

---

### Post by ghostdog74 on 2008-03-11
> **slavik said:**
> ```

I dunno what has to go instead of ARGV[1]

[code]
import sys
arg=sys.argv[1]
..

```
and of couse, you and i know that unless there's really no other way, using code like that is not portable.

---

### Post by bvmou on 2008-03-12
Actually what I am currently using is exactly as you describe, except I stringify the input number, ie `a`, and pass that to the mtime flag of find.  It is not ideal, what I am doing is just having the program ask "how many days worth of podcasts do you want to keep on the device."

@ghostdog:  The portability question is indeed the issue, it has been working fine as a bash shell and then pythonified, this is more an effort to get all my stuff free of things like hardcoded filepaths and interoperable.  It is amazing though, something like:

cp ~/Desktop/*.mp3 /media/device

comes out (for me) as:

```
osma = os.walk('/home/user/Desktop', True, None)
osmalist = []
for item in osma:
	osmalist.append(item)
for item in osmalist[0][2]:
	if item[-3:] == 'mp3':
		shutil.copy('/home/user/Desktop/'+item, '/media/device'')
```

So

os.system('find ~/podcasts/current -mindepth 2 -mtime '+`a`+' -exec mv {} ~/podcasts/old \;')

is likely to be a bit trickier!

One other ques: how to call shutil.copy(a,b) so that a does not overwrite b when they have the same name?

---

### Post by ghostdog74 on 2008-03-12
> **bvmou said:**
> 
One other ques: how to call shutil.copy(a,b) so that a does not overwrite b when they have the same name?
check for presence of the file first.. if it is , do whatever, like rename it to another name or something.

---

### Post by bvmou on 2008-03-13
Thanks Ghostdog,

That was probably a malformed question; I am trying to do something like shutil.copytree() where I only update new files, something closer to 'cp -ru /folder /destination'.  I will definitely post whatever solution I come up with and any help is appreciated.

I also may not want to go overboard with the interoperability stuff; I was thinking that for my own linux solution I could have a constant dynamically updated folder of symbolic links that would be generated on the basis of newness and size parameters.

Any further thoughts appreciated, as is the help to this point.

---

### Post by dwblas on 2008-03-13
A standard example of os.path.walk() with an isfile added would work.  You can run this as is to see how it processes the directories recursively.  Note os.path.walk() works with a callback.  In this example processDirectory() will be called for each directory encountered```
def processDirectory ( args, dirname, filenames ):
    new_dir ="/backup" + dirname
    print 'Directory',dirname
    for filename in filenames:
       print '     File',filename
       ##if not os.path.isfile( os.path.join(new_dir, filename) ):
          ##copy file or whatever
top_level_dir = "/usr/local"
os.path.walk(top_level_dir, processDirectory, None )
```

---

