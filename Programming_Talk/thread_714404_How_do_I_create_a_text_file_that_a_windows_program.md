---
title: "How do I create a text file that a windows program can read?"
date: 2008-03-03
forum: Programming Talk
---

### Post by jsym on 2008-03-03
Hello fellow ubutuians,

I hope you can help me.

I need to output simple text to a file such that a windows program that I am running via wine can read the data.  I understand that windows and linux format text files differently (something about lines breaks), but I don't know any of the details of the difference.  So how do these file formats differ and (more importantly) how can I force windows formatting on a linux text file?

I am using eclipse and g++; the following code can easily serve as an example for the kind of files I need to create:
```
#include <fstream>
#include <string>

using namespace std;

int main(void)
{
	string outFileName;
	outFileName="pajekTest.net";
	ofstream outFile0(outFileName.data(), ios::out);
	outFile0 << "*Vertices  3" << endl;
	outFile0 << "1 \"A\"" << endl;
	outFile0 << "1 \"B\"" << endl;
	outFile0 << "1 \"C\"" << endl;
	outFile0 << "*Arcs" << endl;
	outFile0 << "1 2 3" << endl;
}
```
[I can't see why it matters, but the program that I need to read this data file is called [[COLOR="Blue"]_Pajek_[/COLOR]]("http://vlado.fmf.uni-lj.si/pub/networks/pajek/").  It is an open source tool for mapping complicated networks.  It runs nicely under wine.]

---

### Post by LaRoza on 2008-03-03
The only thing that differs is how newlines are defined.

Use "\r\n" for newlines.

Windows (DOS actually) uses Carriage Returns and Line Feeds (CR LF) and *nix uses Line Feeds for defining new lines. And Mac (as far as I know, I don't know about recent edition) use Carriage Returns.

---

### Post by jsym on 2008-03-03
Perfect.

Dropping "\r" (the carriage-return escape sequence) at the end of every line seems to clear up the problem nicely.

For anyone else that happens this way, the working version of the original code I passed above is:
```
#include <fstream>
#include <string>

using namespace std;

int main(void)
{
	string outFileName;
	outFileName="pajekTest.net";
	ofstream outFile0(outFileName.data(), ios::out);
	outFile0 << "*Vertices  3\r" << endl;
	outFile0 << "1 \"A\"\r" << endl;
	outFile0 << "1 \"B\"\r" << endl;
	outFile0 << "1 \"C\"\r" << endl;
	outFile0 << "*Arcs\r" << endl;
	outFile0 << "1 2 3\r" << endl;
}

```

Thanks for the speedy reply LaRoza, I was worried I'd be feeling like an idiot over something small for hours!:)

---

### Post by nanotube on 2008-03-03
well, see if pajek reads the file you are currently generating... i think it probably won't have any problems. just about the only software that still has problems reading '\n' linebreak files is notepad. even wordpad has no problems with '\n' linebreaks. :)

---

### Post by LaRoza on 2008-03-03
> **jsym said:**
> 
Thanks for the speedy reply LaRoza, I was worried I'd be feeling like an idiot over something small for hours!:)

No problem, it is interesting how such small things can cause hiccups.

---

### Post by nanotube on 2008-03-03
ah heh i see that you /did/ test and /were/ having problems. never mind, then. but you can submit a bug report to pajek and tell them about their failure to properly parse unix-style linebreaks (and thus probably mac-style (\r only) ones as well)...

also, by the way, looking at the pajek site, it seems that it's not open source... they only provide binaries, and it's "free for non-commercial use"...

---

### Post by aks44 on 2008-03-03
One more thing to care about would be character encoding. Ubuntu (and probably most other Linux distros) now uses UTF-8 as their main encoding.

Windows programs still mostly use local code pages (eg. ISO-8859-1). This will be a problem if you carelessly use any character outside the legacy (7 bit) ASCII range.

Unicode-enabled programs should detect the file encoding by looking at the first bytes of the file if there is an [UTF Byte Order Mark (BOM) header]("http://en.wikipedia.org/wiki/Byte_Order_Mark"). If the file doesn't start with a BOM header, the program will generally assume that the file uses whatever default ANSI encoding that your Windows is configured against.

With Unicode-disabled (pun intended) programs, you're out of luck...

---

### Post by schiznik on 2008-03-03
to convert between unix and dos text files, theres a little tool called dos2unix, its part of sysutils iirc.

---

