---
title: "Rename thousand+ font files"
date: 2009-05-31
forum: Programming Talk
---

### Post by ricardisimo on 2009-05-31
Sorry to be such a newbie leach, but would someone be willing to write a script that would rename the skedillion fonts that I currently have in my .fonts folder. For unknown reasons, they have been names like "AC______.ttf" instead of whatever the real name is (in this case, "Acadian". Is it possible to write a script that would call up each font's actual name and use that info to rename the file?

Do linux filenames ever need to be contiguous? Which characters are forbidden? Thanks.

---

### Post by slavik on 2009-05-31
normally, you wouldn't use anything outside of a-zA-Z.-_ and sometimes @() and space

as for renaming a file, it is easy if there is a simple way to get the name of the font and what not.

---

### Post by ricardisimo on 2009-06-01
"Easy" is a relative term, I'm assuming. It's certainly easy for me to double-click on a font file and read the font name in the first line of Font Viewer. I wouldn't have the slightest clue how one would call up that information directly from the file, however. Any clues?

---

### Post by unutbu on 2009-06-01
ricardisimo, to avoid a tragic error (on my part), first backup your ~/.fonts folder. If you have the space, this would do:
```

rsync -a ~/.fonts/ ~/.fonts_bak/
```

Then save this script to ~/bin/rename_fonts.py
[PHP]
#!/usr/bin/env python
import os
import sys
from subprocess import Popen,PIPE,STDOUT

import optparse
usage = 'usage: %prog [options]'
parser = optparse.OptionParser(
    usage=usage)
parser.add_option('-p', '--path', dest='path', 
                  default='.',
                  help='path to font dir', 
                  metavar='PATH')
parser.add_option('-x', dest='execute', 
                  action='store_true',
                  default=False,
                  help='execute', 
                  )
(opt, args) = parser.parse_args()

def uniquify(path,sep='_'):
    path=os.path.normpath(path)
    num=0
    newpath=path
    idx=path.find('.')
    if idx>0:
        part1=path[:idx]
        part2=path[idx:]
    else:
        part1=path
        part2=''
    while os.path.isdir(newpath) or os.path.isfile(newpath): 
        newpath=part1+sep+str(num)+part2
        num+=1
    return newpath

def standardize_name(astr):
    astr=astr.replace('\\','')
    astr=astr.replace(' ','_')
    return astr

cmd='fc-cat -v'
proc=Popen(cmd, shell=True, stdout=PIPE, stderr=open('/dev/null'))
output=proc.communicate()[0].split('\n')
filenames=[]
newnames=[]
for line in output:

# A line looks like this:
# "Phetsarath_OT.ttf" 0 "Phetsarath OT:familylang=en:style=Regular:stylelang=en:fullname=Phetsarath OT:fullnamelang=en:slant=0:weight=80:width=100:foundry=unknown:index=0:outline=True:scalable=True:charset=  |>^1!|>^1!P0oWQ |>^1!|>^1!|>^1!!!!%# !!71$!#>r1F3y?4!!K?&   !!!)$      )KG/~ !!!.%   9WIlj    !!!Q3    {y]9#8?/cS5fQdN !!#0GM>T@D#y#fx   !!#eW  !!#3H !!!!&      !!#AL      !!!W5 :lang=aa|ast|ay|bi|br|ch|co|da|de|en|es|et|eu|fi|fj|fo|fr|fur|fy|gd|gl|gv|ho|ia|id|ie|io|is|it|lb|lo|mg|nb|nds|nl|nn|no|nr|nso|oc|om|pt|rm|sma|smj|so|sq|ss|st|sv|sw|tn|ts|vo|vot|wa|xh|yap|zu:fontversion=65536:capability=otlayout\\:lao :fontformat=TrueType:decorative=False"

    if line.startswith('"'):
        row=line.split('"')
        filename,num,info_str=row[1],row[2],row[3]
        _,ext=os.path.splitext(filename)
        info_list=info_str.split(':')
        common_name=info_list[0]
        if common_name=='.dir':
            continue
        full_name=None
        style=None
        filenames.append(filename)
        for info in info_list:
            if info.startswith('style='):
                style=info.replace('style=','')
            if info.startswith('fullname='):
                full_name=info.replace('fullname=','')
                full_name=full_name.split(',')[0]
        if full_name:
            if full_name.startswith(common_name):
                newname=standardize_name('%s%s'%(full_name,ext))
            else:
                newname=standardize_name('%s_%s%s'%(common_name,full_name,ext))
        elif style:
            newname=standardize_name('%s_%s%s'%(common_name,style,ext))
        else:
            newname=standardize_name('%s%s'%(common_name,ext))
        newnames.append(newname)

namedict=dict(zip(filenames,newnames))
os.chdir(opt.path)
filelist=os.listdir(opt.path)
errors=[]
for afile in filelist:
    try:
        print(afile,namedict[afile])
        if opt.execute:
            os.rename(afile,uniquify(namedict[afile]))
    except KeyError:
        errors.append(afile)

if errors:
    print('These files are left unchanged:')
    for error in errors:
        print(error)
[/PHP]
Make it executable:
```

chmod 755 ~/bin/rename_fonts.py
```

Run it like this:
```

rename_fonts.py -p ~/.fonts
```

This command does not rename anything. But you should see output like this:

```
('VeraMono.ttf', 'Bitstream_Vera_Sans_Mono.ttf')
('VeraMoIt.ttf', 'Bitstream_Vera_Sans_Mono_Oblique.ttf')
('VeraIt.ttf', 'Bitstream_Vera_Sans_Oblique.ttf')
('VeraMoBI.ttf', 'Bitstream_Vera_Sans_Mono_Bold_Oblique.ttf')
('shalosti.pfb', 'Shalom_Stick.pfb')
('boecklin.pfb', 'ArnoldBoecklin_ExtraBold.pfb')
('victoria.pfb', 'Victoriana_Display_SSi_Regular.pfb')
These files are left unchanged:
tempofon.license
crillee.license
carrickc.license
```

On each line of the form (A,B), A is the current file name, and B is the proposed new name. If the proposed new names are satisfactory, then run
```

rename_fonts.py -p ~/.fonts -x
```

This will rename the files.

Finally, run
```

fc-cache -f -v ~/.fonts
```

to make the newly renamed fonts available to the system

---

### Post by Volt9000 on 2009-06-01
Ah crud... I spent all this time whipping up this bash script and someone beat me to it.

Oh well, here it is anyways, in case anyone's interested. Not as elegant as the Python solution, and a bit hacky, but dammit, it's one of my first real bash scripts and I'm bloody proud of it. :D

```

#!/bin/sh

for fontfile in *.ttf; do
    echo -n Processing $fontfile...
    font2c $fontfile temp.c > /dev/null
    newfontfile=$(cat temp.c | grep 'char s_' | head -4 | tail -1 | awk -F '"' '{print $2}' | tr ' ' '_')
    newfontfile=$newfontfile.ttf
    if [ "$fontfile" = "$newfontfile" ]; then
        echo "\t\tSkipping-- file is already properly named."
    else
        mv $fontfile $newfontfile
        echo "\t\tDone."
    fi
done

rm temp.c

```

Copy the above code into a file, chmod +x it and run. I tested this myself and it seems to work well.

---

### Post by unutbu on 2009-06-02
Thanks for posting your script, Volt9000. You used an interesting method I didn't know about.

---

### Post by MichaelSammels on 2009-06-02
Not sure if this has been mentioned, but try GPRename:

```
sudo apt-get install gprename
```

---

### Post by ricardisimo on 2009-06-04
GPRename can't call up file info. Thunar is actually a better option for basic batch file renaming, in my humble opinion.

unutbu: To what does the tilde refer at the very start of your code? In other words, what folder is this: "~/bin/rename_fonts.py"? Is that just my /bin folder, or /usr/bin or is it suggesting that I should make a new "bin" folder within /home/ricardisimo? Thanks.

---

### Post by unutbu on 2009-06-04
ricardisimo, tilde (~) is an abbreviation for /home/ricardisimo. So ~/bin means /home/ricardisimo/bin. If you do not already have one, it is a good idea to make this directory, because any executable you put in there will automatically be "in your PATH".

Whenever you type a command into the shell (terminal), the shell searches for a program with that name in your PATH. 

Thus, if you put rename_fonts.py in ~/bin, then you can run it from the terminal by simply typing

```
rename_fonts.py -p ~/.fonts
```

instead of the longer
```
/home/ricardisimo/rename_fonts.py -p ~/.fonts

```
or
```

/path/to/rename_fonts.py -p ~/.fonts

```
(depending on where you put it.)

---

### Post by ricardisimo on 2009-06-04
Cool. Thanks. Should it be ~/bin or ~/.bin? Hidden or not? Does it matter? Thanks again, and I'm going to try this out in a few moments.

---

### Post by unutbu on 2009-06-04
It must be ~/bin to have it be automatically put in your PATH.
Type 
```

echo $PATH
```
to see what directories are in your PATH.

---

### Post by ricardisimo on 2009-06-04
```
:~$ echo $PATH
/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games
```
I don't see /home/ricardisimo/bin here. Is that because I have yet to chmod it?

---

### Post by ricardisimo on 2009-06-04
Something's off:
```
:~$ chmod 755 ~/bin/rename_fonts.py
:~$ rename_fonts.py -p ~/.fonts
bash: rename_fonts.py: command not found
```

---

### Post by unutbu on 2009-06-04
Close the gnome-terminal and open another terminal.
If ~/bin did not exist when gnome-terminal was launched, then ~/bin would not have been added to your PATH.

---

### Post by MadCow108 on 2009-06-04
volt9000 bash script fails on some files on my pc.
In some files the line fetched with head -4 tail -1 is empty

a fix would be to use the output of font2c which probably finds the fontname with higher reliability:

```

#!/bin/bash
for ffile in *.ttf
do
	echo "processing $ffile..."
	output=`font2c $ffile temp.c`
	newfontfile=`echo $output | sed -e "s/.*FontName is (\([^\)]*\).*/\1/"`
	newfontfile=$newfontfile.ttf
    if [ "$ffile" = "$newfontfile sds" ]; then
        echo -e "\t\tSkipping-- file is already properly named."
    elif [ "$newfontfile" = "" ]; then
    	echo "Extracting of fontname failed!!"
    else
        mv $ffile $newfontfile
        echo -e "\t\tDone."
    fi
done

rm temp.c

```

---

### Post by Volt9000 on 2009-06-04
> **MadCow108 said:**
> volt9000 bash script fails on some files on my pc.
In some files the line fetched with head -4 tail -1 is empty

a fix would be to use the output of font2c which probably finds the fontname with higher reliability:

```

#!/bin/bash
for ffile in *.ttf
do
	echo "processing $ffile..."
	output=`font2c $ffile temp.c`
	newfontfile=`echo $output | sed -e "s/.*FontName is (\([^\)]*\).*/\1/"`
	newfontfile=$newfontfile.ttf
    if [ "$ffile" = "$newfontfile sds" ]; then
        echo -e "\t\tSkipping-- file is already properly named."
    elif [ "$newfontfile" = "" ]; then
    	echo "Extracting of fontname failed!!"
    else
        mv $ffile $newfontfile
        echo -e "\t\tDone."
    fi
done

rm temp.c

```

Ah, yes.
Well unfortunately my script isn't that robust. I did test it on all my font files and it seemed to work well, but of course, it relies on the fact that the format of the font files will be consistent (and for my files they were.)

Thanks for the heads up, though!

---

### Post by ricardisimo on 2009-06-05
On neither of my computers is /home/ricardisimo/bin mentioned when I run "echo $PATH". I've restarted the computers several times by now, so certainly if that folder was going to be in my PATH it should have happened by now. How do I force it to be so?

---

### Post by unutbu on 2009-06-05
Open the file ~/.profile. Does it have this code in it?

```
# set PATH so it includes user's private bin if it exists
if [ -d "$HOME/bin" ] ; then
    PATH="$HOME/bin:$PATH"
fi

```
If not, add it to your ~/.profile. 
Later on in that file you should also have a line which says
```

export PATH
```

Save and exit the text editor. Log out, then log back in.
Open a terminal and type
```

echo $PATH
```

If ~/bin in still not in your PATH, please post your ~/.profile.

---

### Post by ricardisimo on 2009-06-05
It doesn't say "export PATH" anywhere. The code you cited is there, but that's the end of the text in .profile. Do I just add an extra line that says "export PATH"?

---

### Post by unutbu on 2009-06-05
Yes. Add 
```

export PATH

```
to the end of your ~/.profile.

---

### Post by MadCow108 on 2009-06-05
.profile is only read by login shells.
and only if no .bash_profile or .bash_login exist.

If you want it permanently in your path with your usual bash-shell you need to add it to the .bashrc

---

### Post by unutbu on 2009-06-05
~/.profile is read once when you log in to a GNOME desktop.
~/.bashrc is read each time you open a terminal.

Since the PATH need only be set once, it seems to make sense to define the PATH in ~/.profile.

---

### Post by ricardisimo on 2009-06-06
Yay! It's working! Thank you so very much.

The overwhelming majority of the fonts are being renamed to exactly what the name of the font is, which is what I was seeking. However, about 1% are returning either gobbledeygook which doesn't appear in it's title in Font Viewer, at least:
```
('aggstock.ttf', '\xc3\x84ggstock,\xc6\x92ggstock_\xc3\x84ggstock.ttf')
``` and ```
('Bl?jbytesdep?.ttf', 'Bl\xc3\xb6jbytesdep\xc3\xa5,Bl?jbytesdep?_Bl\xc3\xb6jbytesdep\xc3\xa5.ttf')
```
Or it's being renamed to several of its variants or just repeating itself:
```
('SIGNETRO.ttf', 'Signet_Roundhand_ATT,Signet_Roundhand_CE_ATT_Signet_Roundhand_ATT_Italic.ttf')
```
Like I said, these are not the names that appear in Font Viewer.

Any thoughts? Honestly, it's few enough that I could easily go back and change them by hand in no time. I'm just curious if the script is doing what you thought it would do. Thanks again.

---

### Post by unutbu on 2009-06-06
ricardisimo, I'm glad to hear the script mainly worked for you.

I think I can modify the script to improve the renaming in the cases you posted.
Which would you prefer:
```

aggstock.ttf --> Äggstock.ttf
Bl?jbytesdep?.ttf --> Blöjbytesdepå.ttf
```

or 
```

aggstock.ttf --> Aggstock.ttf
Bl?jbytesdep?.ttf --> Blojbytesdepa.ttf
```

In order to fix this, it would help to see some output from you. Please post:```


fc-cat -v | grep ggstock
fc-cat -v | grep jbytesdep
fc-cat -v | grep Signet_Roundhand

```

---

### Post by ricardisimo on 2009-06-08
Wow. I had no idea there would actually be - basically - HTML options! If I had to choose, I'd say no special characters (in case I need some Mac or Windows user to install one of my fonts), first letter capitalized.

Tell me this: Is it also possible to add abbreviated extra info, like "B" for bold, "BI" for bold & italics, etc.? Not knowing how font files categorize themselves, I wouldn't know if that's info that could be called up or not.

Also, please tell me that this is at least fun for you. I'm very grateful, and one day, when the kids are older, I'd love to spend some time learning programming and code, but not for a while.

```
:~/.fonts$ fc-cat -v | grep ggstock
/usr/share/X11/fonts: No such file or directory
"aggstock.ttf" 0 "Äggstock,ƒggstock:familylang=en,en:style=Regular:stylelang=en:fullname=Äggstock,ƒggstock:fullnamelang=en,en:slant=0:weight=80:width=100:foundry=unknown:index=0:outline=True:scalable=True:charset=  bW.9^|>^1!>0{]q !!!!#!)pTF!9PXp!!!%#    !!K?&   !!!)$      !!!!j !!#0G !!.)#      !!#6I  !!!%#     :lang=fj|ho|ia|ie|io|nr|om|so|ss|st|sw|ts|xh|zu:fontversion=65536:fontformat=TrueType:decorative=False"
/usr/share/fonts/truetype/ttf-malayalam-fonts: No such file or directory
```
```
:~/.fonts$ fc-cat -v | grep jbytesdep
/usr/share/X11/fonts: No such file or directory
"Bl?jbytesdep?.ttf" 0 "Blöjbytesdepå,Bl?jbytesdep?:familylang=en,en:style=Normal,oby&#269;ejné,Standard,&#922;&#945;&#957;&#959;&#957;&#953;&#954;&#940;,Regular,Normaali,Normál,Normale,Standaard,Normalny,&#1054;&#1073;&#1099;&#1095;&#1085;&#1099;&#1081;,Normálne,Navadno,Arrunta:stylelang=ca,cs,de,el,en,fi,hu,it,nl,pl,ru,sk,sl,eu:fullname=Blöjbytesdepå,Bl?jbytesdep?:fullnamelang=en,en:slant=0:weight=80:width=100:foundry=unknown:index=0:outline=True:scalable=True:charset=  |>]~6P0oWP9WIli P2w[b(7y@T(7y@T!!!%#!#>r4!!7W3      !!!)$      #xwbC !!!.%   9WIlj    !!#0G     !!!W5  !!#6I   !!!!W    :lang=fj|ho|ia|id|ie|io|nr|om|so|ss|st|sw|ts|vo|xh|zu:fontversion=65536:fontformat=TrueType:decorative=False"
/usr/share/fonts/truetype/ttf-malayalam-fonts: No such file or directory
```
```
:~/.fonts$ fc-cat -v | grep SIGNETRO.ttf
/usr/share/X11/fonts: No such file or directory
"SIGNETRO.ttf" 0 "Signet Roundhand ATT,Signet Roundhand CE ATT:familylang=en,pl:style=Italic,Kursywa:stylelang=en,pl:fullname=Signet Roundhand ATT Italic,Signet Roundhand CE ATT Kursywa:fullnamelang=en,pl:slant=100:weight=80:width=100:foundry=agfa:index=0:outline=True:scalable=True:charset=  |>^1!|>^1!P0oWQ |>^1!|>^1!|>^1!!!!%#lTKe<Glr$9lZhN&OovPT!!K?&   !!!)$      9;*l$ !!#0GM>RAd#y#fx   !!!W5  !!#3H !!!!&      !!#6I!a(Q)       !!#AL    !!K?&   !!+Qp!!!!5       :lang=aa|ast|ay|bi|br|bs|ch|co|cs|da|de|en|es|et|eu|fi|fj|fo|fr|fur|fy|gd|gl|gv|ho|hr|hu|ia|id|ie|io|is|it|lb|mg|nb|nds|nl|nn|no|nr|nso|oc|om|pl|pt|rm|sk|sl|sma|smj|so|sq|ss|st|sv|sw|tn|tr|ts|vo|vot|wa|wen|xh|yap|zu:fontversion=131072:fontformat=TrueType:decorative=False"
/usr/share/fonts/truetype/ttf-malayalam-fonts: No such file or directory
```

---

### Post by unutbu on 2009-06-08
ricardisimo, I'd be glad to try to modify the script to get the renamings exactly as you'd prefer. I'll need your help to do so, however; see below. I should also warn you that there appear to be some inconsistencies in the way font information is represented in the output of fc-cat. Since my script is based on parsing the output of fc-cat, this might mean my script is incapable of coming up with renamings which are satisfactory in all cases. But anyway, I'm willing to try if you're interested.

First the easy parts: 

Capitalization is no sweat. 
Using just the first name before a comma: no sweat
Removing all accents: a little harder, but I think I know how to do it.

Now the hard part:

I could change all occurrences of "bold" or "Bold" --> "B", and and "Italics" --> "I", but then ArnoldBoecklin_ExtraBold.pfb would become ArnoldBoecklin_ExtraB.pfb, which looks a little strange to me. Perhaps ArnoldBoecklin_XB.pfb would be better, but down this road lies a slippery slope. Should ParkAvenue_Normal.ttf be renamed ParkAvenue_N.ttf? Should WindsorDemi_Regular.pfb become WindsorDemi_R.pfb? and then what about PostAntiqua_Roman.pfb? 

There are so many choices, I'm not sure what would look best.

Could you run 
```

rename_fonts.py -p ~/.fonts > output.txt
```

then edit output.txt to show (at least for some of them) how you'd prefer the renamings to appear, and then post output.txt as an attachment? Then run
```

fc-cat -v | bzip2 > fc-cat.out.bz2
```

and post fc-cat.out.bz2 as an attachment too.
> 
Also, please tell me that this is at least fun for you.  

Thanks for your concern. It is gratifying to help people. But rest assured, I wouldn't do it if I weren't also having fun. Most of the time I just hope I'm doing more good than harm :)

---

### Post by seeminglee on 2009-06-10
While bash script is always fun to write, I'd like to suggest an alternative solution. There's an AIR app called .merlin that will do exactly what you asked for and more. 

The software can read and process OTF, TTF and Type1 (AFM, PFM, PFB, INF) files. In addition to automatically renaming fonts' filenames to match the font names, it includes toggleable user-options to check for font duplicates and will offer to group fonts with the same first-letter together in their own folder: i.e. for example, Bell Gothic, Bembo, Bodoni and Briem Script will be moved to a folder named "B" and you'll find Caslon, Chaparral and Clarendon in a folder named "C", etc.

**Quick review of the app**

I tried this app out quickly and let it run through the entire Adobe Font Folio OTF edition and some ancient Emigre PFB ruins and even some of my own creation from Fontographer and merlin processed all of them very quickly without a hitch.

Hope this helps.

Cheers,
SML

The only thing that might bother some folks is how the renaming works when the type foundry's name is part of the fonts' name. All of the fonts with ITC prefix like ITC Officina, ITC Stone, ITC Isadora, for example, are renamed to Officina, Stone and Isadora respectively but kept the foundry's name with ITCAvantGarde, ITCFranklinGothic and ITCGaramond - which suggests that the software is smart enough to detect the potential for disasters, for example, if it had otherwise turned AdobeGaramond, ITC Garamond in addition to Monotype and Stempel into a single cut. gasp :)
What is unclear though is if the software has logic put to place to anticipate for these kinds of errors, or if it's simply a table that require / allow updates where necessary. 

Overall, the software performs quite well does exactly as expected. Compared to Extensis FontDoctor (the prof app for Mac+Win), merlin's performance is quite good. It's built using AIR, so you can run it pretty much run it anywhere as well. 

**1. Download and install Adobe AIR**

In order to run .merlin, you'll need the AIR runtime 1.5 or above. You can get and the installer for Linux is available at: .

[http://get.adobe.com/air/]("http://get.adobe.com/air/")

After the the download is completed, go to the folder where you've downloaded the file, change permission on the file and make it executable, then run the installer:

```

$ cd ~/Downloads
$ chmod +x AdobeAIRInstaller.bin
$ ./AdobeAIRInstaller.bin

``` 

Adobe AIR puts itself as the first item under Accessories, though in practice you rarely need to touch it.

**2. Install .merlin**

Go to [http://blog.coursevector.com/merlin]("http://blog.coursevector.com/merlin") and click on the link that says Download Now (1.8.0) 

When the download finishes (about 350k), the program will run automatically and an Adobe AIR prompt will ask if you wish to install the program, etc. It then installs itself under its own menu entry. 

Uninstallation of AIR apps are done using the Aodbe AIR Uninstaller, which is in your Accessories menu.

**A little bit OT but related: apowerful GUI renamer with metadata extraction and RegEx handling** (works with EXIF, MP3 tags etc but wont' do fonts)

I recently had to rename thousands of files as according their metadata (mp3 tags, jpeg exif, folder location, etc). Because of the complexity fo the operation, I looked for a GUI tool that will do it and I found a nitfy one at that caled Métamorphose ([http://file-folder-ren.sourceforge.net]("http://file-folder-ren.sourceforge.net"). The UI can use some improvements though the elements have been rearranged in version 2 (which is in beta right now) which makese it a tad bit easier.

It won't do any good i you are looking to manipulate fonts metadata, but I thought that it's worth mentioning since since I have been looking for something like it for a long time and only just found out about it a week ago.

---

### Post by unutbu on 2009-06-10
Thank you for this information regarding .merlin and Métamorphose, seeminglee.
It sounds a lot better than my ad hoc hackery. :)

---

### Post by ricardisimo on 2011-01-12
Oh, my goodness! I cannot believe that I never thanked unutbu and seeminglee for all of your help here. I realize it has been several years now, but this thread was very helpful and educational. A million thanks. Take care.

---

