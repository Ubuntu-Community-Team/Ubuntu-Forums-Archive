---
title: "Problems with drag and drop into terminal.. Don't think I'm nuts."
date: 2011-04-15
forum: Programming Talk
---

### Post by Jonas thomas on 2011-04-15
Ok.. Here's the deal...
I'm putting the finishing touches on my homework which reads a filename for data entered at a terminal prompt.

Anyway I was dragging a file from the file browser and for what ever reason it stopped working....  It sort of has me stumped at the moment because I really can't figure out what happened.
I can drag the file here.... No problem... See...
file:///media/0AFD-2385/LAB07/input1.cpp

But... when I drag into my terminal nothing... I thought perhaps something was hosed with my do loop and still nothing...

#include <stack> //*4*
#include <string>
#include <iostream>
#include <fstream>
#include <vector>
using namespace std;
class stackElement
{
   public:
    int lineNumber;
    int position;
    char c;
};


```
int main()

{
	string fileName;
	cout << "Lets see whats going wrong: ";
		getline (cin,fileName); //*1*
.........

```

I'm running 10.04 32 bit.. and it recently did updates.. Is there a possible that a update has hosed up the works??

Or... did I think hose something up in my code... I think not... This is really curious...
Anyone any ideas? 
Only thing I remember that I added a vector after it stopped working... Time for a quick test...

---

### Post by Jonas thomas on 2011-04-15
Ok.. 
I tried another testfile..

> #include <iostream>
#include <string>
using namespace std;

int main()
{
    string testname;
    cout <<"Enter a file name:";
    getline(cin, testname);

    cout <<testname;
}

If I run the program from code::blocks the drag and drop does not work.. If I directly run from the executable from a the terminal... Drag and drop works...
Hmm.. I'm backporting the latest and greatest code::blocks and I did see and update recently... perhaps its that... Strange...

---

### Post by Jonas thomas on 2011-04-16
This is really irritating...
I was dragging and dropping blissfully away and then it stops working after doing some updates.  I now don't think this is a code::blocks issues.

I was dragging a file from Nautilus 2.30.1 and dropping into an xterm window and nothing was happening.
The settings in my IDE environment was: xterm -T $TITLE -e

I changed settings from xterm to: gnome-terminal -t $TITLE -x  
(hopefully I got that right) and the file name drops but I get single quotes around the filepath which is hosing up my program IOW
'file:///home/jonas/Desktop/input1.cpp' I'm also getting an annoying message about running an executable(probably can suppress that with the correct terms) [Edit... That can be fixed by going Places->Home folder, then Edit->Preferences->Behavior and selecting Executable Text Files and clicking on the "run executable text files when they are opened"]
I suppose fix my program to strip the '' but that's a hack.

I really s/b be focusing on my homework.. But this is really bugging me.

I'm thinking this is a new bug in Nautilus or I'm doing something really stupid.. Is anyone having similar issues with a drag and drop? (10.04 32bit)

---

### Post by Jonas thomas on 2011-04-16
I need to move along here and took the path of least resistance... Ie code around the issue..  I suspect that there is a bug in nautilus that got introduced in the last couple of days..
For what ever reason, stopped working totally in xterm and I had to this to read a file from gnome-terminal
```

int main()

{
	string fileName;
	do
	{
		cout << "Please enter the file to analyze: ";
		getline (cin,fileName); //*1*

		//for some weird reason my drag and drop started producing ' at the beginning and end of the file name
		//which was hosing up the works... I don't think this should be happening.
		//I hacked around the issue to get this done.
		//I believe this to be a bug in Nautilus 2.30.1 in Linux... It happens ;(
		cout <<fileName<<endl;
		int temp = fileName[0];
		cout << temp << "  temp number"<<endl;

		if (fileName[0]==39)//'
        {
            fileName.erase(0,1);
            cout <<fileName<<endl;
        }

        cout <<">"<<fileName<<"<"<<endl;
        cout <<fileName[fileName.size()-1]<<endl;

        if (fileName.size()>2)
        {
            if (fileName[fileName.size()-2]==39)//'getting a ' with a space at the end.
            {
                fileName.erase(fileName.size()-2,2);
                //fileName= "file://"+fileName;

                cout <<fileName<<endl;
            }
        }

        cout <<fileName<<endl;

		string accumulationStr = "";
        string LineOfCode;
		stackElement stackElem;

		vector <string> VectCode;
		cout <<"beginning:"<<fileName.c_str()<<":end"<<endl;

		ifstream sourceFile(fileName.c_str());
```


If it's not a bug.. feel free to tell me what I'm doing wrong.

---

