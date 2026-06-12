---
title: "Automatically detect executable type and run with suitable program."
date: 2008-11-08
forum: Outdated Tutorials &amp; Tips
---

### Post by quinn on 2008-11-08
This is a little kludgy perl hack i concocted because i have both old DOS games and newer windows programs, and was tired of manually picking whether it needed wine or dosbox when running from Nautilus, and i thought i would share it with anyone else who was in a similar situation to me. This script also accounts for .Net executables, so running programs in Mono should still work.

This script, naturally, requires Wine, Dosbox, and Mono to be installed. While it will run without any of these, it will error out when trying to run a Windows, DOS or .Net executable, respectively.
I've tested this on Intrepid, but it should, in theory, work on any distro with a sufficiently modern findutils.
```
#!/usr/bin/perl

$DOS_PROG="dosbox -exit";
#DOS_PROG="dosbox"; #uncomment this if you'd prefer DOSBOX not to automatically exit when the program finishes.
$WIN_PROG="wine";
#$WIN_PROG="winefix"; #uncomment this if you have winefix installed.
$DOTNET_PROG="mono";


$RUNFILE = "$ARGV[0]";
$FILE_TYPE=`file \"$RUNFILE\"`;
$FILE_DIR=`dirname \"$RUNFILE\"`;
$COMMAND_LINE=join(' ',@ARGV);

if ($FILE_TYPE =~ m/MS-DOS executable/) {
	if ($FILE_TYPE =~ m/Mono\/\.Net assembly/) {
		$RUN_COMMAND = $DOTNET_PROG;
	} elsif ($FILE_TYPE =~ m/for MS Windows/) {
		$RUN_COMMAND = $WIN_PROG;
	} elsif ($FILE_TYPE =~ m/for MS-DOS/ || $FILE_TYPE =~ m/for OS\/2/) {
		$RUN_COMMAND = $DOS_PROG; #I've encountered at least one DOS-compatible exe that identifies as OS/2. Given that there's no proper OS/2 compatability layer, this seems like a harmless assumption.
	} else {
		print "$RUNFILE: Unrecognized EXE Format.";
		exit 1;
	}
} else {
	print "$RUNFILE: Not an MS-DOS Executable file.\n";
	exit 1;
}

chdir ($FILE_DIR);
exec("$RUN_COMMAND \"$COMMAND_LINE\"");

```

To use this, copy the above code, and paste it into a file called exe-detect.pl

Then, from the command line, run

```
chmod +x exe-detect.pl
sudo cp exe-detect.pl /usr/local/bin/ #Optional

```

Finally, in a nautilus window:

Right click any EXE file
Go to "Open With" tab, and click "Add"
Expand the Custom Command area at the bottom of that dialog, and select wherever you placed the exe-detect.pl file
Click Add to confirm
Click the option button by the exe-detect.pl in the program list

OPTIONAL: If you want to be able to mark an EXE file as runnable, and execute it directly from the command line, this code should do the trick:

```
 sudo update-binfmts --install exe-detect /usr/local/bin/exe-detect.pl --magic 'MZ'

```

And you should be ready to go! 
While this has worked for all the programs i've tried it with, it's entirely possible that something will confuse this script. If that happens, please send me the output of "file <exe name>". Thank you, and happy EXE running!

---

