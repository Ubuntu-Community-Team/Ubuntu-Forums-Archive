---
title: "HOWTO : developing flex with gvim"
date: 2008-04-02
forum: Programming Talk
---

### Post by delfick on 2008-04-02
hello.

for quite a few years I've been interested in flash, and have moved from developing flash stuff in the flash ide with no actionscript whatsoever, to doing stuff in the ide with an extensive amount of actionscript, to using a combination of just actionscript2 and [kagswf](http://kagswf.tensus.net/) (as in no ide :)) to now using flex (actionscript3 and mxml)

Anyway, it took quite a bit of searching to be able to do this in linux (more so when I was working with actionscript2 than with flex) and there is quite a few threads on this forum asking for ways to develop flash in linux.

So I've decided to put down here how I've got gvim to play nice with actionscript3 and mxml.


**First** download the flex3 sdk from here :
[http://www.adobe.com/products/flex/flexdownloads/index.html](http://www.adobe.com/products/flex/flexdownloads/index.html)

then extract that to wherever you want,  on my computer I've chosen :
/usr/local/flex


Then in the terminal, we need to make the mxmlc compiler executable :
$ sudo chmod +x /usr/local/flex/bin/mxmlc

then we need to make that folder part of your $PATH so that you only have to type "mxmlc" in the terminal to run it. To do this we first open this file /etc/bash.bashrc :
$ gksudo gedit /etc/bash.bashrc

(I'm not sure if this is the best place to put this (it doesn't work when i put it in ~/.bashrc), hopefully someone can clarify that :))

and add the following at the top :
export PATH=${PATH}:/usr/local/flex/bin

then when you have your flex project you can use mxmlc to compile your main mxml file (I assume you already know how to make a flex project, if not, this place [here](http://livedocs.adobe.com/flex/) is a good place to start (it's where I started :)))

mxmlc usage is as follows :
mxmlc [options] <target mxml file>

**Second** we set up gvim to have proper syntax highlighting for the .mxml and .as files.

here is my ~/.vim folder which holds the actionscript2, actionscript3 and mxml syntax files, as well as my custom colours file (you can use whatever colours you want) :
[http://delfick755.googlepages.com/hiddenVim.tar.gz](http://delfick755.googlepages.com/hiddenVim.tar.gz)

then to make sure that the right syntax highlighting is applied to those files, make sure the following is in your ~/.vimrc file

```

au BufNewFile,BufRead *.mxml set filetype=mxml
au BufNewFile,BufRead *.as set filetype=actionscript
syntax on

```

and some nice things to have in your ~/.vimrc (unrelated to actionscript)
```

set number
set nocompatible
set history=50          " keep 50 lines of command line history
set ruler               " show the cursor position all the time
set showcmd             " display incomplete commands
set showmode            " display the mode you are in everytime
set mouse=a             " mouse works in all modes
set incsearch           " do incremental searching
set showmatch           " balancing brackets like in emacs
set wrap!               " linewrapping off
set ignorecase          " evident
set nostartofline       "to keep the cursor at the same horizontal location when
set tabstop=4           " number of spaces that a <Tab> in the file counts for
set laststatus=1        " show status line only if there are more than one windows
set shiftwidth=4        " size of tabs by default
set backup              "  backUps!!
set title               "see filename in Xterm title
imap ZZ <esc>:wq!<cr>   " ZZ saves and leaves as well in insert mode
set autoindent
set smartindent
source $VIMRUNTIME/mswin.vim  " make it behave like windows

```

**Thirdly** change the mime information so that you don't get annoying messages about the file not being the expected type when you double click .as files. 

Go into ~/.local/share/mime/packages (or create that directory first if it doesn't exist)

then add a file called actionscript.xml with the following in it

```
<?xml version="1.0" encoding="UTF-8"?>
	<mime-info xmlns="http://www.freedesktop.org/standards/shared-mime-info">
		<mime-type type="text/actionscript">
			<sub-class-of type="text/plain"/>
			<comment>Actionscript Source Code</comment>
			<glob pattern="*.as"/>
			<glob pattern="*.as2"/>
			<glob pattern="*.as3"/>
		</mime-type>
	</mime-info>
```

then add another file called mxml.xml with the following in it

```
<?xml version="1.0" encoding="UTF-8"?>
	<mime-info xmlns="http://www.freedesktop.org/standards/shared-mime-info">
		<mime-type type="text/mxml">
			<sub-class-of type="text/xml"/>
			<comment>Mxml Source Code</comment>
			<glob pattern="*.mxml"/>
		</mime-type>
	</mime-info>
```

then do
```
update-mime-database ~/.local/share/mime
```

(if you want this to be a system wide setting then do the same, but in /usr/local/share/mime)

**Fourthly** install the linux debugger flash player and the flashtracer extension so you can see trace statements

first, download the debugger flash player from here [http://download.macromedia.com/pub/flashplayer/updaters/9/flash_player_9_linux_dev.tar.gz](http://download.macromedia.com/pub/flashplayer/updaters/9/flash_player_9_linux_dev.tar.gz)

Unpack it to the desktop, then unpack the archive found in the plugin/debugger folder, and run the flashplayer-installer file

Then install the firefox FlashTracer extension, as found here [https://addons.mozilla.org/en-US/firefox/addon/3469](https://addons.mozilla.org/en-US/firefox/addon/3469)

and create a file in your home folder called mm.cfg and add the following to it
```
TraceOutPutFileName=/home/iambob/.macromedia/Flash_Player/Logs/flashlog.txt
ErrorReportingEnable=1
TraceOutputFileEnable=1
MaxWarnings=100

```

(change "iambob" to your username)

Then in the options for flashtracer, make the output file equal to the first line above, so for me it would be "/home/iambob/.macromedia/Flash_Player/Logs/flashlog.txt"

...

Hopefully this has helped some people, I certainly would have liked to have this back when I started trying to figure out how to make this work :)

have fun.

---

### Post by bobbwhy on 2008-04-03
Hey Delfick, very nice tutorial.. I got along alright.. but when I tried compiling the sample descriptor* application that came with the sdk.. 
no dice.. Unsupported file type was thrown.

Please let me know what your system configuration is? 

thanks!
Robert

---

### Post by delfick on 2008-04-03
> **bobbwhy said:**
> Hey Delfick, very nice tutorial..

thnx :)

> Unsupported file type was thrown.

so what exactly are you doing to get this error?
and what exactly is the error ? 
:)

---

### Post by bobbwhy on 2008-04-04
Thanks for reply... 
Ok.. so I downloaded the sdk .. 
put it in /usr/local/flex

changed the permissions to 755 (and anyway they are all under my username so should not matter)

(did not yet alter path.. but from /usr/local/flex/samples did this: 

../bin/mxmlc descriptor-sample.xml

it churned away for a sec.. then gave me: 

loading configuration file /usr/local/flex/frameworks/flex-config.xml

Error: Unsupported file type: /usr/local/flex/samples/descriptor-sample.xml


Now.. I am very new to flex.. so maybe I am missing something very simple.. ?  I will keep looking.. meanwhile.. thanks very much.

---

### Post by delfick on 2008-04-04
mxmlc compiles mxml files, not xml files :)

---

### Post by bandito40 on 2008-04-10
This tutorial worked great.  After trying swfmill, adst, elcipse which all gave one problem or another, I can finally start building flash movies. 

Thanks,

Carl

[http://www.gaihosa.com](http://www.gaihosa.com)

---

### Post by delfick on 2008-04-10
> **bandito40 said:**
> This tutorial worked great.  After trying swfmill, adst, elcipse which all gave one problem or another, I can finally start building flash movies. 

I know the feeling :)

> Thanks,

no probs :)

I'm glad it helped.

---

### Post by rtoot3 on 2008-05-18
ok well i did what you said and it worked for one file. but one of the action script files i made didnt work

this is what the file said

var message = "Hi there Flash!";
var FirstName = "Ryland"
trace(message);
trace("Hi there, " + FirstName + ", nice to meet you.");

i saved it as testflash.as to my desktop and typed mxmlc testflash.as into the terminal here is what the output said:

Loading configuration file /usr/local/flex/frameworks/flex-config.xml
/home/ryland/Desktop/testflash.as: Error: A file found in a source-path must have an externally visible definition. If a definition in the file is meant to be externally visible, please put the definition in a package.

do you know wats wrong?

---

### Post by delfick on 2008-05-19
you need a bit more in the file than that :)

you have two options, either use mxml to describe the stage via something like this
```
<?xml version="1.0" encoding="utf-8"?>
<mx:Application
	xmlns:mx="http://www.adobe.com/2006/mxml"
	width="100%" height="100%">

	<mx:Script>
		<![CDATA[
			
			import flash.events.*;
			
			[Bindable]
			private var message:String = "hello";

			private var message1:String = "hello";
			private var message2:String = "hi";

			private function changeMessage(event:Event):void
			{
				if (message == message1)
				{
					message = message2;
				}
				else
				{
					message = message1;
				}
			}

			
		]]>
	</mx:Script>

	<mx:Panel width="50%" height="50%">
		<mx:TextArea width="100%" height="100%" id="logger">
			<mx:text>{message}</mx:text>
		</mx:TextArea>
	</mx:Panel>

	<mx:Button label="change the message" click="changeMessage(event)"/>

</mx:Application>

```

I recommend going through this [http://examples.adobe.com/flex2/inproduct/sdk/explorer/explorer.html](http://examples.adobe.com/flex2/inproduct/sdk/explorer/explorer.html)
and for more thorough documentation, [http://livedocs.adobe.com/flex/2/langref/mx/controls/package-detail.html](http://livedocs.adobe.com/flex/2/langref/mx/controls/package-detail.html)

or even [http://livedocs.adobe.com/flex/2/langref/package-summary.html](http://livedocs.adobe.com/flex/2/langref/package-summary.html)

and definitely this [http://livedocs.adobe.com/flex/201/html/Part1_languages_049_1.html](http://livedocs.adobe.com/flex/201/html/Part1_languages_049_1.html)

and this [blog.flexexamples.com](blog.flexexamples.com)

:)

or you can do it via pure actionscript. But I can't remember off the top of my head how exactly to do that. Here is something I've adapted from something i saw the other day (10 minutes, 13 seconds into [http://www.gotoandlearn.com/player.php?id=73](http://www.gotoandlearn.com/player.php?id=73))

```
package
{
	import flash.display.*;
	import flash.text.*;
	import mx.controls.Button;
	import mx.containers.Panel;
	import flash.events.Event;

	//swf metadata
	[SWF(width="600", height="400", backgroundColor="#FFFFFF", framerate="30")]

	public class Start extends Sprite
	{
		private var theTF:TextField;
		private var theButton:Button;
		private var thePanel:Panel

		[Bindable]
		private var message:String;

		private var message1:String = "hello there";
		private var message2:String = "second message";

		public function Start():void
		{
			thePanel = new Panel();
			theTF = new TextField();
			theButton = new Button();

			thePanel.percentWidth = 50;
			thePanel.percentHeight = 50;
			addChild(thePanel);

			theTF.text = message;
			//i think you need to use event handlers for it to actually change when message changes
			thePanel.addChild(theTF);

			theButton.label = "label";
			//then you use event handlers (easy, but I can't remember how) to make it do something when clicked on
			thePanel.addChild(theButton);
		}

		private function changeMessage(event:Event):void
		{
			if (message == message1)
			{
				message = message2;
			}
			else
			{
				message = message1;
			}
		}
	}
}

``` 

though it doesn't work and I have no idea why, and don't have time atm to figure out why...
(but when mxml is compiled, it is converted into actionscript classes before being compiled, so anything you can do in mxml, you can do in actionscript)

morale of the story, it's easier to do it in mxml :)

and example slightly more related to your question is this

```
<?xml version="1.0" encoding="utf-8"?>
<mx:Application
	xmlns:mx="http://www.adobe.com/2006/mxml"
	width="100%" height="100%"
	creationComplete="init()">

	<mx:Script>
		<![CDATA[

			private function init():void
			{
				var theMessage:String = "Hi there Flash!";
				var firstName:String = "Ryland";
				trace(theMessage);
				trace("Hi there, " + firstName + ", nice to meet you.");
			}


		]]>
	</mx:Script>

</mx:Application>

```

Also, I've updated the tutorial to show how to be able to read trace messages...

---

### Post by rtoot3 on 2008-05-19
wait one more thing. so am i supposed to write mxml code and then use the mxmlc command to turn it into flash, or do i write action script and then use the mxmlc command to turn it into flash?

sorry if i missed some obvious information

---

### Post by delfick on 2008-05-19
you can use either.

but mxml tends to be easier to layout things (and it's easier to bind things and use event handlers in mxml)

I suggest going through this [http://www.adobe.com/devnet/flex/?tab:samples=1](http://www.adobe.com/devnet/flex/?tab:samples=1)

because there's only so much I can explain, mainly because I'm not too good at explaining things, and I don't have much spare time atm, and I'm still very much learning myself :)

---

### Post by rtoot3 on 2008-05-21
oops, lol, sorry i looked more at your first post on this, it was very obvious, i was being stupid

---

### Post by delfick on 2008-05-21
> **rtoot3 said:**
> oops, lol, sorry i looked more at your first post on this, it was very obvious, i was being stupid

that's alright :)

---

### Post by rtoot3 on 2008-05-22
ok i dont know if im just stupid, or flex doesnt like me, but i put in this code

<?xml version="1.0"?>
<!-- mxml\DefProp.mxml -->
<mx:Application xmlns:mx="http://www.adobe.com/2006/mxml" >

    <!-- Omit the default property. -->
    <mx:ComboBox> 
        <mx:ArrayCollection>
            <mx:String>AK</mx:String>
            <mx:String>AL</mx:String>
            <mx:String>AR</mx:String>
        </mx:ArrayCollection>
    </mx:ComboBox>
    
    <!-- Explicitly speficy the default property. -->
    <mx:ComboBox> 
        <mx:dataProvider>
            <mx:ArrayCollection>
                <mx:String>AK</mx:String>
                <mx:String>AL</mx:String>
                <mx:String>AR</mx:String>
            </mx:ArrayCollection>
        </mx:dataProvider>
    </mx:ComboBox>    
</mx:Application>

and saved it as HelloWorld.as, then i typed in the terminal mxmlc HelloWorld.as and this is what the output was

Loading configuration file /usr/local/flex/frameworks/flex-config.xml
Error: unable to open 'HelloWorld.as'

Use 'mxmlc -help' for information about using the command line.

help me in my stupidness!

---

### Post by rtoot3 on 2008-05-22
ok sorry again for my stupidness, i found out that was because i didnt cd to where i saved it, but this time with the same file(except i renamed it snackytreat.as) i did mxmlc command and it comes up with this

/home/ryland/Desktop/snackytreat.as(3): col: 4 Error: Label must be a simple identifier.

<mx:Application xmlns:mx="http://www.adobe.com/2006/mxml" >
   ^

/home/ryland/Desktop/snackytreat.as(3): col: 17 Error: Attribute is invalid.

<mx:Application xmlns:mx="http://www.adobe.com/2006/mxml" >
                ^

/home/ryland/Desktop/snackytreat.as(6): col: 4 Error: Label must be a simple identifier.

<mx:ComboBox>
   ^

/home/ryland/Desktop/snackytreat.as(12): col: 1 Error: Syntax error: expecting identifier before xmltagstartend.

</mx:ComboBox>
^
WHY DOES EVERYTHING GO WRONG FOR ME!?!?!? :(

---

### Post by delfick on 2008-05-23
you have to save mxml files with a .mxml extension :)

also. a forum better suited to flash/actionscript/flex specific questions would be over here [http://board.flashkit.com/board/](http://board.flashkit.com/board/) :)

---

### Post by rtoot3 on 2008-05-23
k ill go there, and thank you so much! youve been a huge help, just one more thing though, the default background color for the flash objects is like a grayish color, do you know how to change that?

---

### Post by delfick on 2008-05-24
> **rtoot3 said:**
> k ill go there, and thank you so much! youve been a huge help,

no probs :)

>  just one more thing though, the default background color for the flash objects is like a grayish color, do you know how to change that?

[http://livedocs.adobe.com/flex/201/html/app_container_064_04.html](http://livedocs.adobe.com/flex/201/html/app_container_064_04.html)

:)

---

### Post by Q-ro on 2008-06-28
**wich sdk should i download ?? i see 2 one for windows one for mac, so i dont know wich should i download :/**

---

### Post by delfick on 2008-06-28
hmm, weirdly the link in my first post pointed to the downloads for the flex builder...

the sdk can be found here [http://www.adobe.com/products/flex/flexdownloads/index.html](http://www.adobe.com/products/flex/flexdownloads/index.html)

(I've updated the first post to point there)

---

### Post by Q-ro on 2008-06-29
**ok all was fine till i get to the part of fash tracer :S, unfortunately there seems not to be a version for fire fox 3, when i try to install it, i got a message saying that is incompatible, so, is there another way ?? or do i have to wait till a new version of the add-on is release ?**

---

### Post by delfick on 2008-06-29
I have version 2.3 [http://www.sephiroth.it/firefox/](http://www.sephiroth.it/firefox/) installed and it seems to work with firefox 3 :)

---

### Post by Q-ro on 2008-07-01
**The page seems not to be working or at least not for me, and other thing, the gvim folder, what do i do with it after checking that the files have what they are spoused to had ?? ( i don't really get it, am i spoused to put in on some folder, by now is on my desktop )**

---

### Post by delfick on 2008-07-01
> **Q-ro said:**
> The page seems not to be working or at least not for me


which one ??
all seem to work for me ...

>  and other thing, the gvim folder, what do i do with it after checking that the files have what they are spoused to had ?? ( i don't really get it, am i spoused to put in on some folder, by now is on my desktop )
.

I'm gonna take a guess that you're new to linux (that's fine, I was the same nearly two years ago)

firstly, '~' means your home folder.
secondly a folder with a '.' as the first character in it's name means it's a hidden folder
thirdly, programs generally store user settings in hidden folders in your home folder

so ~/.vim is a hidden folder called ".vim" in your home folder (/home/<username>) 

so just copy the .vim folder and .vimrc file as is into your home folder :)

(.vimrc contains settings for vim and the .vim folder holds the actionscript and mxml syntax files and my colour style

:)

---

### Post by Q-ro on 2008-07-01
**ok thanks a lot :), well and not totally new, but still don't get much of the symbolism like that you where talking about ("~") any way, thanks a lot now i'll begin flex developing :) .**

---

### Post by delfick on 2008-07-02
> **Q-ro said:**
> **ok thanks a lot :), well and not totally new, but still don't get much of the symbolism like that you where talking about ("~") any way, thanks a lot now i'll begin flex developing :) .**

no probs :)

have fun :)

---

### Post by pingnak on 2008-11-14
Good tutorial!

Here's another version of the same help in a more persistent form, along with JEdit setup instructions.  

Also integration of make/preprocessor with MXMLC or Flash from the command line, and various scripting examples for the same.  Both Linux and Windows examples.

[http://flex2cpp.sourceforge.net/index.html](http://flex2cpp.sourceforge.net/index.html)

---

### Post by delfick on 2008-11-14
> **pingnak said:**
> Good tutorial!

Thankyou :)

> Here's another version of the same help in a more persistent form, along with JEdit setup instructions.  

Also integration of make/preprocessor with MXMLC or Flash from the command line, and various scripting examples for the same.  Both Linux and Windows examples.

[http://flex2cpp.sourceforge.net/index.html](http://flex2cpp.sourceforge.net/index.html)

ahh, he finally has that site back up again :) (was down for a while)

I actually use that in a couple of projects.
not heavily, but it is useful for a couple of things
(especially to quickly make a build without trace messages in it)

:)

---

### Post by tinny on 2008-11-29
Anyone know how to generate Actionscript SOAP web service clients (wsdl introspection) from a WSDL? (On linux of course) I can do this on Windows using Flex builder, but it would be a life saver for me if I could do it on Linux.

Thanks in advance.

---

### Post by delfick on 2008-11-29
> **tinny said:**
> Anyone know how to generate Actionscript SOAP web service clients (wsdl introspection) from a WSDL? (On linux of course) I can do this on Windows using Flex builder, but it would be a life saver for me if I could do it on Linux.

Thanks in advance.

hmm, not sure.

You might want to start a new thread about that

or even in a forum committed to flash (i.e. [http://board.flashkit.com/board/](http://board.flashkit.com/board/) )

:)

---

### Post by pepinot on 2008-11-29
Hi,

I've a problem with my FlexSDK installation on Linux Ubuntu Hardy and I don't find anything about it.

So I installed Gvim, Flex SDK and Java JRE, I wrote un little code in actionscript and then I then I launch mxmlc and then... an error. THE error.

```
GC Warning: Out of Memory!  Returning NIL!
mxmlc: line 47: 22014 Erreur de segmentation  java $VMARGS -jar "$FLEX_HOME/lib/mxmlc.jar" +flexlib="$FLEX_HOME/frameworks" "$@"

```

So I require your help. 

Thanks

---

### Post by delfick on 2008-11-29
> **pepinot said:**
> Hi,

I've a problem with my FlexSDK installation on Linux Ubuntu Hardy and I don't find anything about it.

So I installed Gvim, Flex SDK and Java JRE, I wrote un little code in actionscript and then I then I launch mxmlc and then... an error. THE error.

```
GC Warning: Out of Memory!  Returning NIL!
mxmlc: line 47: 22014 Erreur de segmentation  java $VMARGS -jar "$FLEX_HOME/lib/mxmlc.jar" +flexlib="$FLEX_HOME/frameworks" "$@"

```

So I require your help. 

Thanks

hmm, that's an interesting error.

you too might want your own thread for that :p

(though I suggest, this forum [http://www.adobe.com/cfusion/webforums/forum/categories.cfm?forumid=60&catid=585](http://www.adobe.com/cfusion/webforums/forum/categories.cfm?forumid=60&catid=585))

:)

---

### Post by rtoot3 on 2008-12-09
hey! im back! a while ago i read this tutorial and it worked great. but i wanted to learn action script to make games. i soon quit  because in every tutorial i found for as, it would say something like "create a new movie clip named..." and i didnt know how to do that with code. i just recently learned how so im gonna start learning again. but when i tried to compile it using mxmlc map.as and it said i didnt have that command. then i checked to see if i had it installed still, and i do. why wont it work?
```

ryland@ryland-desktop:~$ cd /home/ryland/Desktop
ryland@ryland-desktop:~/Desktop$ mxmlc map.as
bash: mxmlc: command not found
ryland@ryland-desktop:~/Desktop$ cd /usr/local/flex/bin
ryland@ryland-desktop:/usr/local/flex/bin$ ls
aasdoc      adl.exe     asdoc       copylocale.exe  fdb         optimizer
aasdoc.bat  adt         asdoc.exe   digest          fdb.exe     optimizer.exe
acompc      adt.bat     compc       digest.exe      jvm.config
acompc.bat  amxmlc      compc.exe   fcsh            mxmlc
adl         amxmlc.bat  copylocale  fcsh.exe        mxmlc.exe
ryland@ryland-desktop:/usr/local/flex/bin$ 

```

---

### Post by delfick on 2008-12-09
> **rtoot3 said:**
> when i tried to compile it using mxmlc map.as and it said i didnt have that command. then i checked to see if i had it installed still, and i do. why wont it work?

I would guess it's either not in your PATH or it doesn't have executable permissions.

Firsty, executable permissions, try 
$sudo chmod +x /usr/local/flex/bin/mxmlc

if that doesn't work, then open up /etc/bash.bashrc
$gksudo gedit /etc/bash.bashrc

and add 
export PATH=${PATH}:/usr/local/flex/bin

near the top.

then restart your terminal and theoretically it should work :p :)

---

### Post by rtoot3 on 2008-12-09
thanx, it worked, by the way, what is bash.bashrc?

---

### Post by delfick on 2008-12-10
> **rtoot3 said:**
> thanx

no probs :)

> by the way, what is bash.bashrc?

small possibility I'm wrong, but it's a file that contains system wide configuration settings for the bash shell :)

[http://en.wikipedia.org/wiki/Bash](http://en.wikipedia.org/wiki/Bash)

---

### Post by OmegaWarrior on 2009-01-21
I hope you can help me because I'm about to go crazy over this.  I did steps 1-3 and then I get stuck:
> **delfick said:**
> 
**Fourthly** install the linux debugger flash player and the flashtracer extension so you can see trace statements

first, download the debugger flash player from here [http://download.macromedia.com/pub/flashplayer/updaters/9/flash_player_9_linux_dev.tar.gz](http://download.macromedia.com/pub/flashplayer/updaters/9/flash_player_9_linux_dev.tar.gz)

Simple enough...

> **delfick said:**
> Unpack it to the desktop, 
...so far so good...
> **delfick said:**
> then unpack the archive found in the plugin/debugger folder,
...okay, I unpacked libflashplayer.so.tar.gz to libflashplayer.so.

> **delfick said:**
>  and run the flashplayer-installer file
...what flashplayer-installer file?  the libflashplayer.so file?  Ubuntu says there is no type associated with .so files, and from what I understand, so = Shared Object which doesn't sound like an executable file and there were no other files in that path.  Me confused.  Delfick explain.

---

### Post by delfick on 2009-01-21
> **OmegaWarrior said:**
> ...what flashplayer-installer file?  the libflashplayer.so file?  Ubuntu says there is no type associated with .so files, and from what I understand, so = Shared Object which doesn't sound like an executable file and there were no other files in that path.  Me confused.  Delfick explain.

hmm, it seems they've changed it............

just put it in ~/.mozilla/plugins and it should work :)

---

### Post by OmegaWarrior on 2009-01-21
> **delfick said:**
> hmm, it seems they've changed it............

just put it in ~/.mozilla/plugins and it should work :)

So it's not me? *whew* Thank You;  and thank You for answering so quickly.

---

### Post by delfick on 2009-01-21
> **OmegaWarrior said:**
> hank You;

no probs :)

> and thank You for answering so quickly.

well, you seem to post when I'm at my computer :)
(and [gmail-notify](apt:gmail-notify) means I know about emails as they come)

---

