---
title: "Need Help Compiling Audio Waveform Generator WAV2PNG"
date: 2007-05-01
forum: Programming Talk
---

### Post by kentbye on 2007-05-01
**UPDATE**: *WW helped me to successfully compile the audio waveform generator WAV2PNG. More details on how down below. Thanks!*

The [Freesound project]("http://freesound.iua.upf.edu/") uses an open source script called WAV2PNG for audio visualizations.  You input a *.wav file to the script, and it creates a PNG of the audio waveform.

[This waveform]("http://freesound.iua.upf.edu/samplesViewSingle.php?id=2523") is an example of the output of the script.

Bram de Jong has posted the code online [here.]("http://freesound.iua.upf.edu/files/wav2png.tar.gz")

I'm having trouble compiling the C++ code since I'm used to dealing with doing ./configure, make and make install to get something working.  To complicate matters it depends upon the [AnyOption C++ class]("http://www.hackorama.com/anyoption/") for parsing complex commandline options.

It also has dependencies on libsndfile and libgd2, but I was able to successfully install these with the following commands:
sudo apt-get install libsndfile-dev  **EDIT** -- This should have been "sudo apt-get install libsndfile1-dev"
sudo apt-get install libgd2-xpm **EDIT** -- This should have been "sudo apt-get install libgd2-xpm-dev"

I was wondering if someone could give me some step-by-step tips for getting this WAV2PNG script compiled and working.

I've got a ~/bin/wav2png folder with the following six files in it, and need to know what to do next. 
anyoption.cpp
anyoption.h
demo.cpp
gpl.txt
main.cpp
Makefile

Thanks,
-Kent.

---

### Post by WW on 2007-05-01
Try running **make** in that directory and see if it compiles successfully.

EDIT: Install the package **libgd2-xpm-dev** first.

---

### Post by kentbye on 2007-05-01
I tried running make and executing the makefile, but received the errors listed down below.

My hunch is that I need to some how compile the two anyoption files (anyoption.cpp & anyoption.h) since the WAV2PNG main.cpp file depends upon the anyoption command line parsing definitions.  The [anyoption page]("http://www.hackorama.com/anyoption/") isn't really clear for what I'm even supposed to do with the three files, and so they may even need to be in a separate folder for all I know.

**~/bin/wav2png$ make**
g++ -c -O2 -Wall -pedantic anyoption.cpp
make: g++: Command not found
make: *** [anyoption.o] Error 127

**~/bin/wav2png$ sudo chmod +x Makefile**
**~/bin/wav2png$ ./Makefile**
./Makefile: line 1: g++: command not found
./Makefile: line 2: -c: command not found
./Makefile: line 3: -lgd: command not found
./Makefile: line 6: all:: command not found
./Makefile: line 7: CC: command not found
./Makefile: line 7: LDFLAGS: command not found
./Makefile: line 7: EXEC: command not found
./Makefile: line 7: anyoption.o: command not found
./Makefile: line 9: static:: command not found
./Makefile: line 10: CC: command not found
./Makefile: line 10: LDFLAGS: command not found
./Makefile: line 10: EXEC: command not found
./Makefile: line 10: -static: command not found
./Makefile: line 12: main.o:: command not found
./Makefile: line 13: CC: command not found
./Makefile: line 13: CXXFLAGS: command not found
./Makefile: line 13: main.cpp: command not found
./Makefile: line 15: anyoption.o:: command not found
./Makefile: line 16: CC: command not found
./Makefile: line 16: CXXFLAGS: command not found
./Makefile: line 16: anyoption.cpp: command not found
./Makefile: line 18: clean:: command not found
rm: cannot remove `./*.o': No such file or directory
./Makefile: line 20: EXEC: command not found
rm: missing operand
Try `rm --help' for more information.

**EDIT**
I also tried moving the three anyoption files (anyoption.cpp, anyoption.h & demo.cpp) to another folder, and compile it with the cc command, but I got the following error:

**~/bin/anyoption$ cc anyoption.cpp**
cc: error trying to exec 'cc1plus': execvp: No such file or directory

Any other help on this is greatly appreciated!
Thanks,
-Kent.

---

### Post by WW on 2007-05-01
It appears that you do not have the g++ compiler installed.  Do this:
```

sudo apt-get install build-essential

```

The instructions in the **Makefile** will take care of compiling anyoption.cpp and main.cpp, and linking them together to create the executable program.

EDIT:  You don't run a Makefile.  The Makefile is read by the **make** command; it defines the dependencies of the files, and tells **make** which programs to run to build the final program.

---

### Post by kentbye on 2007-05-01
**UPDATED AGAIN**: New errors with  **make** down below.

Thanks for the tips so far.
I can tell that I'm getting closer, but I'm still getting some errors.

I did a **sudo apt-get install build-essential** -- but I had run [B]sudo apt-get install g++
[/B] just before you're update so I'm not sure if that changes anything.

[B]~/bin/wav2png$ make
[/B]g++ -c -O2 -Wall -pedantic anyoption.cpp
g++ -c -O2 -Wall -pedantic main.cpp
main.cpp:36:21: error: sndfile.h: No such file or directory
main.cpp: In function &#8216;long int string2color(std::string, gdImage*)&#8217;:
main.cpp:75: error: no matching function for call to &#8216;transform(__gnu_cxx::__normal_iterator<char*, std::basic_string<char, std::char_traits<char>, std::allocator<char> > >, __gnu_cxx::__normal_iterator<char*, std::basic_string<char, std::char_traits<char>, std::allocator<char> > >, __gnu_cxx::__normal_iterator<char*, std::basic_string<char, std::char_traits<char>, std::allocator<char> > >, <unresolved overloaded function type>)&#8217;
main.cpp: In function &#8216;int main(int, char**)&#8217;:
main.cpp:624: error: &#8216;SNDFILE&#8217; was not declared in this scope
main.cpp:624: error: &#8216;infile&#8217; was not declared in this scope
main.cpp:625: error: &#8216;SF_INFO&#8217; was not declared in this scope
main.cpp:625: error: expected `;' before &#8216;sfinfo&#8217;
main.cpp:628: error: &#8216;SFM_READ&#8217; was not declared in this scope
main.cpp:628: error: &#8216;sfinfo&#8217; was not declared in this scope
main.cpp:628: error: &#8216;sf_open&#8217; was not declared in this scope
main.cpp:633: error: &#8216;sfinfo&#8217; was not declared in this scope
main.cpp:635: error: &#8216;sf_close&#8217; was not declared in this scope
main.cpp:639: error: &#8216;sfinfo&#8217; was not declared in this scope
main.cpp:731: error: &#8216;sf_readf_float&#8217; was not declared in this scope
main.cpp:770: error: &#8216;sf_close&#8217; was not declared in this scope
make: *** [main.o] Error 1

-Kent.

---

### Post by WW on 2007-05-01
Run **make**, like this:
```

$ make

```

---

### Post by WW on 2007-05-01
Ah, you need to install **libsndfile1-dev** (not libsndfile-dev; I don't think there is such a package).

---

### Post by kentbye on 2007-05-01
Okay -- successfully did a **sudo apt-get install libsndfile1-dev** (Seeing the light at the end of the tunnel and thinking that love Ubuntu so far)

So I have less errors.  But still some wierdness:

What say you ol' WW oracle? :)

**~/bin/wav2png$ make**
g++ -c -O2 -Wall -pedantic main.cpp
main.cpp: In function ‘long int string2color(std::string, gdImage*)’:
main.cpp:75: error: no matching function for call to ‘transform(__gnu_cxx::__normal_iterator<char*, std::basic_string<char, std::char_traits<char>, std::allocator<char> > >, __gnu_cxx::__normal_iterator<char*, std::basic_string<char, std::char_traits<char>, std::allocator<char> > >, __gnu_cxx::__normal_iterator<char*, std::basic_string<char, std::char_traits<char>, std::allocator<char> > >, <unresolved overloaded function type>)’
make: *** [main.o] Error 1

---

### Post by WW on 2007-05-01
I also got the error that begins
```

main.cpp:75: error: no matching function for call to &#8216;transform(...

```
I wasn't able to figure out just what the problem is with that line in the code (maybe a true C++ guru can jump in here), but I was able to compile the program by changing line 75 of main.cpp from this:
```

    std::transform(s.begin(), s.end(), s.begin(), std::tolower);

```
to this
```

    std::transform(s.begin(), s.end(), s.begin(), (int (*)(int)) tolower);

```

EDIT: Give it a shot: use a text editor to change line 75 of main.cpp to the line above, and run **make** again.

---

### Post by kentbye on 2007-05-01
Wow.
Let me just say that I'm floored at the Ubuntu community so far.
I'll try making that change and see if I can successfully create a PNG from a WAV file.

Do you know the command line syntax for actually generating a waveform?
Let me know if you have any luck with it.

BTW, I hope to use this as part of a massive collaboratively edited documentary over at [EchoChamberProject.com]("http://www.echochamberproject.com")

---

### Post by WW on 2007-05-01
If it all works, you will see something like this:
```

$ make
g++ -c -O2 -Wall -pedantic anyoption.cpp
g++ -c -O2 -Wall -pedantic main.cpp
g++ anyoption.o main.o -lgd -lsndfile -ljpeg -o wav2png
$

```
The executable program is now called **wav2png**.  Run it with the command **./wav2png**, e.g.
```

$ ./wav2png --help

Usage: wav2png --input wavefile.wav

        Additional options: --width 300 --height 151 --output image.jpg --linecolor ff00aa --backgroundcolor 002222 --zerocolor ff0000 --colorfile filename --padding 2 --verbose true --type jpeg --quality 85
        Short command line switches: -i -w -h -o -l -b -z -c -o

        width: width of PNG (default: 300)
        height: height of PNG (default: 151)
        output: output filename (default: input filename with '.png' appended)
        linecolor: color of waveform lines (default: 323232)
        backgroundcolor: color of background (default: FFFFFF)
        zerocolor: color of line through zero (default: 960000)
                colors are defined like HTML colors in hex
        colorfile: file with (samplePosition,value) pairs for coloring
        padding: padding around the edge
        verbose: true or false
        type: png or jpeg
        quality: jpeg quality between 0 and 100

$

```

So it looks like the simplest version is just
```

$ ./wav2png --input myfile.wav

```
and it will create myfile.wav.png.

---

### Post by WW on 2007-05-01
It worked for me.  The command
```

$ ./wav2png --input poing1.wav

```
created point1.wav.png (attached).

---

### Post by kentbye on 2007-05-01
OMG!  It works!
Thanks a million.

I'm going to explore the command line options to get the pretty colors like Freesound.

There is a way to get the colors of the waveform to relate to the spectral (pitch) content of the waveform. In other words, it will show cold colors for low frequency pitches and hot colors for high frequencies.
Here's an example sinusoid sweep from low to high frequency: [http://freesound.iua.upf.edu/samplesViewSingle.php?id=11]("http://freesound.iua.upf.edu/samplesViewSingle.php?id=11")

Thanks again,
-Kent.

BTW, here's the description from [their technology page.]("http://freesound.iua.upf.edu/technology.php")
"The waveform display uses the spectral content of the wavefiles to color the waveform. A descriptor called 'spectral centroid' (spectral centroid = average frequency, weighted by amplitude, of a spectrum...) is used to derive a color. Basicaly colors towards blue are low frequency and colors towards red are high frequency."

---

### Post by Wybiral on 2007-05-01
I'm not sure why they didn't just allow the uppercase letters in the hex conversion...

```

long hex2dec(char h)
{
	switch(h)
	{
	case 'A': case 'a': return 10;
	case 'B': case 'b': return 11;
	case 'C': case 'c': return 12;
	case 'D': case 'd': return 13;
	case 'E': case 'e': return 14;
	case 'F': case 'f': return 15;
	default:
		{
			char tmp = h - '0';
			if(tmp >= 0 && tmp <= 9)
				return tmp;
			else
				return 0;
		}
	}
}

```

Instead of doing another pass over the entire string to set it to lowercase.

---

### Post by kentbye on 2007-05-01
Has anyone been able to figure out what an input colorfile file should look like for the WAV2PNG colorfile option?

It should define "(samplePosition,value) pairs for coloring," but I'm not savvy enough to know what an example colorfile input file should look like -- or what it can do exactly.

But I wonder -- Is this how Freesound is able to plot colors in the waveform that relate to the spectral (pitch) content of the waveform like in this [example]("http://freesound.iua.upf.edu/samplesViewSingle.php?id=11")?

Thanks,
-Kent.

---

