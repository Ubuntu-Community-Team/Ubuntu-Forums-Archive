---
title: "Really weird C++ error with Ternary Operator"
date: 2012-01-27
forum: Programming Talk
---

### Post by ve4cib on 2012-01-27
I'm working on a piece of C++ and I am getting a fantastically weird error I thought I would share with you:

The class I'm working on is part of a robot vision system.  I use an up-vote/down-vote system to determine if a blob I've detected in the image is a viable candidate for the object we're looking for or not.  You can disable certain categories if they're not needed (e.g. if the objects have a lot of surface noise you may want to disable up/down voting based on how solidly filled the blob is).

Anyway, to determine what the maximum number of votes a blob can have is I have this function (the cout statements were added for debugging).

```

int MultiTarget::GetMaxVotes()
{
    cout << (proportionsDisabled ? 0:1) << endl;
    cout << (fillDisabled ? 0:1) << endl;
    cout << (sizeDisabled ? 0:1) << endl;
    cout << (yRangeDisabled ? 0:1) << endl;
    cout << (uRangeDisabled ? 0:1) << endl;
    cout << (vRangeDisabled ? 0:1) << endl;
    cout << (keyRangeDisabled ? 0:1) << endl << endl;

    return (proportionsDisabled ? 0:1) +
           (fillDisabled ? 0:3) +          // +1 for >.5, >.6, >.7
           (sizeDisabled ? 0:1) +
           (yRangeDisabled ? 0:1) +
           (uRangeDisabled ? 0:1) +
           (vRangeDisabled ? 0:1) +
           (keyRangeDisabled ? 0:1);
}

```

All of the *Disabled variables are bools.  This function is consistently returning 386, and the output from the couts looks like this:

```

0
1
1
1
254
126
1

```

How in the world is "(vRangeDisabled ? 0:1)" returning a value of 126!?  I have never seen anything like this before.  Have any of you?

---

### Post by Arndt on 2012-01-27
> **ve4cib said:**
> I'm working on a piece of C++ and I am getting a fantastically weird error I thought I would share with you:

The class I'm working on is part of a robot vision system.  I use an up-vote/down-vote system to determine if a blob I've detected in the image is a viable candidate for the object we're looking for or not.  You can disable certain categories if they're not needed (e.g. if the objects have a lot of surface noise you may want to disable up/down voting based on how solidly filled the blob is).

Anyway, to determine what the maximum number of votes a blob can have is I have this function (the cout statements were added for debugging).

```

int MultiTarget::GetMaxVotes()
{
    cout << (proportionsDisabled ? 0:1) << endl;
    cout << (fillDisabled ? 0:1) << endl;
    cout << (sizeDisabled ? 0:1) << endl;
    cout << (yRangeDisabled ? 0:1) << endl;
    cout << (uRangeDisabled ? 0:1) << endl;
    cout << (vRangeDisabled ? 0:1) << endl;
    cout << (keyRangeDisabled ? 0:1) << endl << endl;

    return (proportionsDisabled ? 0:1) +
           (fillDisabled ? 0:3) +          // +1 for >.5, >.6, >.7
           (sizeDisabled ? 0:1) +
           (yRangeDisabled ? 0:1) +
           (uRangeDisabled ? 0:1) +
           (vRangeDisabled ? 0:1) +
           (keyRangeDisabled ? 0:1);
}

```

All of the *Disabled variables are bools.  This function is consistently returning 386, and the output from the couts looks like this:

```

0
1
1
1
254
126
1

```

How in the world is "(vRangeDisabled ? 0:1)" returning a value of 126!?  I have never seen anything like this before.  Have any of you?

Post a complete program that exhibits the problem. It looks strange, yes.

---

### Post by ve4cib on 2012-01-27
> **Arndt said:**
> Post a complete program that exhibits the problem. It looks strange, yes.

I can't really post the entire program; this is part of a shared library that consists of a few dozen classes.  But here's some of the relevant code.

The bool variables in the ternary operators are protected members of the AbstractTarget class.  I have another derived class ("Target") that also uses them in the same way and does not have the error I described in my original post.

**MultiTarget.h**
```

#ifndef MULTITARGET_H
#define MULTITARGET_H

#include "darwin/framework/TargetProcessing.h"
#include "darwin/framework/AbstractTarget.h"
#include <string>
#include <iostream>
#include <vector>

namespace Robot
{
    class MultiTarget: public AbstractTarget
    {
        public:
            MultiTarget();
            MultiTarget(const char* name);
            ~MultiTarget();

            // draw the targets' bounding boxes on the provided image
            void DrawBoundingBoxes(cv::Mat &image);

            // print the name, current positions, and pixel sizes of the target in the last frame examined
            void Print();

            // locate this target on the image;
            // returns the number of items found in the scene
            int FindInFrame(cv::Mat &image, cv::Mat *dest);

            std::vector<BoundingBox*> *GetBoundingBoxes(){return this->allTargets;}

        private:

            // the target's pixel dimensions and position
            std::vector<BoundingBox*> *allTargets;

            void Init(const char* name);
            void ClearAllTargets();

            int GetMaxVotes();

    };
}
#endif // MULTITARGET_H

```

**AbstractTarget.h**
This is the class MultiTarget inherits from
```

#ifndef ABSTRACTTARGET_H_INCLUDED
#define ABSTRACTTARGET_H_INCLUDED

#include "darwin/framework/minIni.h"
#include "darwin/framework/TargetProcessing.h"
#include <opencv/cv.h>

namespace Robot
{
    class AbstractTarget
    {
        public:

            // load target properties from an Ini file
            virtual void LoadIniSettings(minIni &ini, const char* section);

            // print out the target's properties
            virtual void Print() = 0;

            // locate this target on the image;
            virtual int FindInFrame(cv::Mat &image, cv::Mat *dest=NULL) = 0;

            // Accessors/Mutators
            void SetDimensions(int realWidth, int realHeight) {this->realWidth = realWidth; this->realHeight = realHeight;}
            void SetYRange(int min, int max) {this->yRange.min = min; this->yRange.max = max;}
            void SetURange(int min, int max) {this->uRange.min = min; this->uRange.max = max;}
            void SetVRange(int min, int max) {this->vRange.min = min; this->vRange.max = max;}

            void SetMarkColour(int r, int g, int b) {this->markColour = cv::Scalar(b, g, r);}

            void SetKeyChannel(int x);
            void SetMinScanLength(int x){this->minScanLength = x;}
            void SetScanThreshold(int x){this->scanThreshold = x;}

            void SetMinPixelHeight(int x){this->minPixelHeight = x;}
            void SetMinPixelWidth(int x){this->minPixelHeight = x;}

            void SetIgnoreTop(int x){this->ignoreTop = x;}
            void SetIgnoreLeft(int x){this->ignoreLeft = x;}
            void SetIgnoreBottom(int x){this->ignoreBottom = x;}
            void SetIgnoreRight(int x){this->ignoreRight = x;}

            void SetProportionsDisabled(bool b){proportionsDisabled = b;}
            void SetFillDisabled(bool b){fillDisabled = b;}
            void SetSizeDisabled(bool b){sizeDisabled = b;}
            void SetYRangeDisabled(bool b){yRangeDisabled = b;}
            void SetURangeDisabled(bool b){uRangeDisabled = b;}
            void SetVRangeDisabled(bool b){vRangeDisabled = b;}
            void SetKeyRangeDisabled(bool b){keyRangeDisabled = b;}

            ThresholdRange *GetYRange(){return &(this->yRange);}
            ThresholdRange *GetURange(){return &(this->uRange);}
            ThresholdRange *GetVRange(){return &(this->vRange);}

            int GetKeyChannel(){return this->keyChannel;}
            int GetMinScanLength(){return this->minScanLength;}
            int GetScanThreshold(){return this->scanThreshold;}

            int GetMinPixelHeight(){return this->minPixelHeight;}
            int GetMinPixelWidth(){return this->minPixelHeight;}

            int GetIgnoreTop(){return this->ignoreTop;}
            int GetIgnoreLeft(){return this->ignoreLeft;}
            int GetIgnoreBottom(){return this->ignoreBottom;}
            int GetIgnoreRight(){return this->ignoreRight;}

            cv::Scalar *GetMarkColour(){return &(this->markColour);}
            std::string *GetName(){return this->name;}

        protected:
            // the target's name
            std::string *name;

            // the target's real-world dimensions
            int realHeight; //mm
            int realWidth;  //mm

            // number of pixels around each edge of the frame where we can ignore results (since they will be noise)
            int ignoreTop;
            int ignoreLeft;
            int ignoreBottom;
            int ignoreRight;

            // max/min yuv parameters
            ThresholdRange yRange;
            ThresholdRange uRange;
            ThresholdRange vRange;

            ThresholdRange *keyChannelRange;

            // scanline parameters
            int keyChannel;
            int minScanLength;
            int scanThreshold;

            int minPixelWidth;
            int minPixelHeight;

            // colour used to mark the target's bounding box on the image
            cv::Scalar markColour;

            // enable/disable different properties to check for
            bool proportionsDisabled;
            bool fillDisabled;
            bool sizeDisabled;
            bool yRangeDisabled;
            bool uRangeDisabled;
            bool vRangeDisabled;
            bool keyRangeDisabled;
    };
}

#endif // ABSTRACTTARGET_H_INCLUDED

```

**AbstractTarget.cpp**
This is the only place in AbstractTarget where the variables in question are used.  minIni is a class for reading/writing .ini configuration files.  I did not write it, but I know that it is not the problem.
```

void AbstractTarget::LoadIniSettings(minIni &ini, const char* iniSection)
{
    if(name==NULL)
        delete name;
    name = new string(ini.gets(iniSection,"Name"));

    realHeight = ini.geti(iniSection,"RealHeight");
    realWidth = ini.geti(iniSection,"RealWidth");

    ignoreTop = ini.geti(iniSection,"IgnoreTop");
    ignoreLeft = ini.geti(iniSection,"IgnoreLeft");
    ignoreBottom = ini.geti(iniSection,"IgnoreBottom");
    ignoreRight = ini.geti(iniSection,"IgnoreRight");

    yRange.min = ini.geti(iniSection,"MinY");
    yRange.max = ini.geti(iniSection,"MaxY");
    uRange.min = ini.geti(iniSection,"MinU");
    uRange.max = ini.geti(iniSection,"MaxU");
    vRange.min = ini.geti(iniSection,"MinV");
    vRange.max = ini.geti(iniSection,"MaxV");

    SetKeyChannel(ini.geti(iniSection,"KeyChannel",1));
    minScanLength = ini.geti(iniSection,"MinScanLength",8);
    scanThreshold = ini.geti(iniSection,"ScanThreshold",50);
    minPixelHeight = ini.geti(iniSection,"MinPixelHeight",10);
    minPixelWidth = ini.geti(iniSection,"MinPixelWidth",10);

    markColour = Scalar(ini.geti(iniSection,"MarkB",0), ini.geti(iniSection,"MarkG",255), ini.geti(iniSection,"MarkR",255));

    sizeDisabled = ini.geti(iniSection,"SizeDisabled");
    proportionsDisabled = ini.geti(iniSection,"ProportionsDisabled");
    fillDisabled = ini.geti(iniSection,"FillDisabled");
    yRangeDisabled = ini.geti(iniSection,"YRangeDisabled");
    yRangeDisabled = ini.geti(iniSection,"URangeDisabled");
    yRangeDisabled = ini.geti(iniSection,"VRangeDisabled");
    keyRangeDisabled = ini.geti(iniSection,"KeyRangeDisabled");
}

```

**MultiTarget.cpp**
The only calls to GetMaxVotes occur in this section of code.  TargetProcessing contains a lot of static functions for doing image processing with OpenCV.
```

int MultiTarget::FindInFrame(Mat &image, Mat *dest)
{
    // clean up the previous round of targets
    ClearAllTargets();

    vector<BoundingBox*> *candidates = TargetProcessing::ScanLine(image, minScanLength, scanThreshold, *keyChannelRange, keyChannel, dest);
    BoundingBox *current;
    int votes;

    double targetRatio = (double)realHeight/(double)realWidth;
    double currentRatio;

    int currentSize;

    cout << "Found " << candidates->size() << " candidates" << endl;
    for(unsigned int i=0; i<candidates->size(); i++)
    {
        current = (*candidates)[i];

        // ignore anything smaller than a certain threshold
        if(current->height >= minPixelHeight && current->width >= minPixelWidth)
        {
            votes = 0;

            currentRatio = (double) current->height / (double) current->width;
            currentSize = current->height * current->width;

            if(!proportionsDisabled)
            {
                // proportions within [0.75,1.25] times the correct size && colours that match
                if((currentRatio < targetRatio && currentRatio * 1.25 >= targetRatio) || (currentRatio > targetRatio && currentRatio * 0.75 <= targetRatio))
                    votes++;

                // proportions are WAY off
                if((currentRatio < targetRatio && currentRatio * 1.25 < targetRatio) || (currentRatio > targetRatio && currentRatio * 0.75 > targetRatio))
                    votes--;
            }

			// each colour channel is acceptable
            if(!yRangeDisabled && yRange.Check(current->avgY))
				votes++;
            if(!uRangeDisabled && uRange.Check(current->avgU))
				votes++;
            if(!vRangeDisabled && vRange.Check(current->avgV))
				votes++;

            // extra vote if the key channel range is good
            if(!keyRangeDisabled)
            {
                switch(keyChannel)
                {
                    case 2:
                        if(keyChannelRange->Check(current->avgV))
                            votes++;
                        break;
                    case 1:
                        if(keyChannelRange->Check(current->avgU))
                            votes++;
                        break;
                    case 0:
                    default:
                    if(keyChannelRange->Check(current->avgY))
                            votes++;
                        break;
                }
            }

            if(!fillDisabled)
            {
                // fill is sufficient
                if(current->fill >= 0.5)
                    votes++;
                if(current->fill >= 0.6)
                    votes++;
                if(current->fill >= 0.7)
                    votes++;

                // fill is insufficient
                if(current->fill <0.5)
                    votes--;
                if(current->fill <0.4)
                    votes--;
                if(current->fill <0.3)
                    votes--;
            }

            // found a better match; use this one
            // THE ERROR IS APPEARING HERE
            cout << "Candidate " << i << " got " << votes << " out of " << GetMaxVotes() << endl;
            if(votes >= GetMaxVotes()/2)
            {
                allTargets->push_back(new BoundingBox(*current));
            }
        }
    }


    // clean up
    //while(!candidates->empty())
    //    delete (*candidates)[candidates->size()-1];
    delete candidates;

    return allTargets->size();
}

int MultiTarget::GetMaxVotes()
{
    cout << (proportionsDisabled ? 0:1) << endl;
    cout << (fillDisabled ? 0:1) << endl;
    cout << (sizeDisabled ? 0:1) << endl;
    cout << (yRangeDisabled ? 0:1) << endl;
    cout << (uRangeDisabled ? 0:1) << endl;
    cout << (vRangeDisabled ? 0:1) << endl;
    cout << (keyRangeDisabled ? 0:1) << endl << endl;

    return (proportionsDisabled ? 0:1) +
           (fillDisabled ? 0:3) +          // +1 for >.5, >.6, >.7
           (sizeDisabled ? 0:1) +
           (yRangeDisabled ? 0:1) +
           (uRangeDisabled ? 0:1) +
           (vRangeDisabled ? 0:1) +
           (keyRangeDisabled ? 0:1);
}


```

---

### Post by Arndt on 2012-01-27
> **ve4cib said:**
> I can't really post the entire program; this is part of a shared library that consists of a few dozen classes.  But here's some of the relevant code.


Trim down the program, then, until you have a minimal one. If the error disappears at some point, maybe then you can discover what causes it. Otherwise, post the minimal program here.

Since it's C++, it could be that the ternary operator has been overloaded to do something weird (can the ternary operator be overloaded?). But you're saying those are just bools.

---

### Post by lisati on 2012-01-27
Perhaps I'm missing something here, not being proficient at C++, but when you have something like **void SetKeyRangeDisabled(bool b){keyRangeDisabled = b;}** perhaps there's something about the way "b" has been (re)defined that's throwing things off....

---

### Post by ve4cib on 2012-01-27
> **lisati said:**
> Perhaps I'm missing something here, not being proficient at C++, but when you have something like **void SetKeyRangeDisabled(bool b){keyRangeDisabled = b;}** perhaps there's something about the way "b" has been (re)defined that's throwing things off....

That shouldn't have an effect.  Defining the body of the function in a header file is basically the same as having the signature in the header and the body in a separate .cpp file.

I just gave up on this whole problem and rewrote the function in question using if-statements instead of ternary operations.  It works now.  But I'm still curious what the issue was in the first place.

Anyway, if you're curious about what the whole program is supposed to do, right now I'm just trying to detect multiple objects in a video file.  Here's a screenshot of the program in action.

[img]http://ubuntuforums.org/attachment.php?attachmentid=211527&stc=1&d=1327700950[/img]

There are three blue objects (the MultiTarget), a yellow thing on the floor, and a red thing resting on top of two of the blue ones.  (The colours are distorted because the video uses the YUV colour space, not RGB.)  The program goes through each frame, finds what it thinks the objects are, and draws boxes around them.

---

### Post by Arndt on 2012-01-27
> **ve4cib said:**
> 

I just gave up on this whole problem and rewrote the function in question using if-statements instead of ternary operations.  It works now.  But I'm still curious what the issue was in the first place.


I say you made the whole thing up.

---

### Post by Hetepeperfan on 2012-01-28
[QUOTE=ve4cib;11645110]
```

int MultiTarget::GetMaxVotes()
{
    cout << (proportionsDisabled ? 0:1) << endl;
    cout << (fillDisabled ? 0:1) << endl;
    cout << (sizeDisabled ? 0:1) << endl;
    cout << (yRangeDisabled ? 0:1) << endl;
    cout << (uRangeDisabled ? 0:1) << endl;
    cout << (vRangeDisabled ? 0:1) << endl;
    cout << (keyRangeDisabled ? 0:1) << endl << endl;

    return (proportionsDisabled ? 0:1) +
           (fillDisabled ? 0:3) +          // +1 for >.5, >.6, >.7
           (sizeDisabled ? 0:1) +
           (yRangeDisabled ? 0:1) +
           (uRangeDisabled ? 0:1) +
           (vRangeDisabled ? 0:1) +
           (keyRangeDisabled ? 0:1);
}

```


At the return statement while adding:
 
```
fillDisabled ?  0:3) +

```
shouldn't the 3 be 1??
```
fillDisabled ?  0:1) +

```

not that this helps for the error your are talking about in the first place.

---

### Post by gateway67 on 2012-01-28
> **arndt said:**
> i say you made the whole thing up.
+1.

---

### Post by ve4cib on 2012-01-28
> **Arndt said:**
> I say you made the whole thing up.

No, I definitely did not make it all up.  Not even I am that bored that I need to make up cryptic errors and post them on message boards for lulz.

Part of me wishes I had made this up though, because then I wouldn't be nearly as confused as I am.  But believe whatever you want.  Not much I can really do to convince you otherwise, is there?

> shouldn't the 3 be 1??
No, it should be a 3.  There's a comment on that line explaining that.  Or at least it explains it for my own record-keeping.  That particular category can contribute up to 3 up-votes, instead of only 1 like the others.

---

### Post by Simian Man on 2012-01-28
Does the problem present itself when you compile with and without optimizations?

---

### Post by trent.josephsen on 2012-01-28
> **ve4cib said:**
> No, I definitely did not make it all up.  Not even I am that bored that I need to make up cryptic errors and post them on message boards for lulz.

Part of me wishes I had made this up though, because then I wouldn't be nearly as confused as I am.  But believe whatever you want.  Not much I can really do to convince you otherwise, is there?

You could post a complete compilable example like you should have done in the first place.

---

### Post by ve4cib on 2012-01-28
> **Simian Man said:**
> Does the problem present itself when you compile with and without optimizations?

Good question.  I really don't know; like I said: I've rewritten the function in question to use if-statements and a series of ++ operations.  It works in that form.  I never thought about checking for compiler optimization issues.

> You could post a complete compilable example like you should have done in the first place.

I'd love to but the function is part of a shared library that I simply cannot publish in its complete form.  And when I try writing smaller examples they work as expected.

I think Simian Man's suggestion that it's some kind of compiler optimization issue may be on the right track.  Or it could have been just a completely random hiccough on my computer.  I'm willing to chalk it up to cosmic rays hitting my RAM circuits, simply because that seems cool.

*shrug* Like I've said a few times, the rewritten version works.  And smaller trial programs work.  So whatever the issue was I've found a way to work around it.  If I ever run into it again I'll be sure to let the internet know.

---

### Post by trent.josephsen on 2012-01-29
You almost certainly have a bug somewhere else in your code that's causing this issue, and if you fail to find it, somebody (possibly you) is eventually going to write more code that causes another issue because of the same bug.

Personally I think lisati is on the right track, but we can't really help without the real code, so... my suggestion is to find somebody you can show it to.

---

### Post by Arndt on 2012-01-29
Have you tried running the program with valgrind?

---

### Post by Simian Man on 2012-01-29
> **ve4cib said:**
> Good question.  I really don't know; like I said: I've rewritten the function in question to use if-statements and a series of ++ operations.  It works in that form.  I never thought about checking for compiler optimization issues.
I asked because you most likely got into some *very* weird undefined behavior somewhere in your code.  Undefined behavior has a tendency to produce different results with and without optimizations.  The other possibility is a compiler bug and most compiler bugs occur during optimization passes.

> **ve4cib]*shrug* Like I've said a few times, the rewritten version works.  And smaller trial programs work.  So whatever the issue was I've found a way to work around it.  If I ever run into it again I'll be sure to let the internet know.[/QUOTE]
You should still find the error unless you have a deadline.  For one, there could be a killer bug lurking that will just mess you up later.  Secondly you've gotten a lot of people here curious.  Though you're probably busy what with the NHL All Star Game and all :).

[QUOTE=Arndt said:**
> Have you tried running the program with valgrind?
That is a very good suggestion.  Valgrind detects many undefined behavior errors.

---

### Post by ve4cib on 2012-01-29
I've re-introduced the buggy code to the shared library, and the same bug has returned.  Good to know it wasn't a transient issue.  I am now seeing the same behaviour I saw in the original post.

When I run with ValGrind I see this output:

```
$ valgrind ./scanline
==1704== Memcheck, a memory error detector
==1704== Copyright (C) 2002-2010, and GNU GPL'd, by Julian Seward et al.
==1704== Using Valgrind-3.6.1 and LibVEX; rerun with -h for copyright info
==1704== Command: ./scanline
==1704== 
Opening video file ../../data/video/yuv_obstacle_scene.avi
==1704== Conditional jump or move depends on uninitialised value(s)
==1704==    at 0x7A570CB: __GI___strcasecmp_l (strcmp.S:243)
==1704==    by 0x79F0F60: __gconv_open (gconv_open.c:70)
==1704==    by 0x79FF106: _nl_find_msg (dcigettext.c:990)
==1704==    by 0x79FF818: __dcigettext (dcigettext.c:654)
==1704==    by 0x8C3D29A: ??? (in /usr/lib/libgtk-x11-2.0.so.0.2400.4)
==1704==    by 0x93BDEB4: g_type_class_ref (in /usr/lib/x86_64-linux-gnu/libgobject-2.0.so.0.2800.6)
==1704==    by 0x93A1DE3: g_object_newv (in /usr/lib/x86_64-linux-gnu/libgobject-2.0.so.0.2800.6)
==1704==    by 0x93A263B: g_object_new (in /usr/lib/x86_64-linux-gnu/libgobject-2.0.so.0.2800.6)
==1704==    by 0x8C3BCAF: gtk_settings_get_for_screen (in /usr/lib/libgtk-x11-2.0.so.0.2400.4)
==1704==    by 0x16EE2034: ??? (in /usr/lib/gtk-2.0/modules/libcanberra-gtk-module.so)
==1704==    by 0x16EE3BEB: gtk_module_init (in /usr/lib/gtk-2.0/modules/libcanberra-gtk-module.so)
==1704==    by 0x8BE8F80: ??? (in /usr/lib/libgtk-x11-2.0.so.0.2400.4)
==1704== 
==1704== Use of uninitialised value of size 8
==1704==    at 0x7A59204: __GI___strcasecmp_l (strcmp.S:2257)
==1704==    by 0x79F0F60: __gconv_open (gconv_open.c:70)
==1704==    by 0x79FF106: _nl_find_msg (dcigettext.c:990)
==1704==    by 0x79FF818: __dcigettext (dcigettext.c:654)
==1704==    by 0x8C3D29A: ??? (in /usr/lib/libgtk-x11-2.0.so.0.2400.4)
==1704==    by 0x93BDEB4: g_type_class_ref (in /usr/lib/x86_64-linux-gnu/libgobject-2.0.so.0.2800.6)
==1704==    by 0x93A1DE3: g_object_newv (in /usr/lib/x86_64-linux-gnu/libgobject-2.0.so.0.2800.6)
==1704==    by 0x93A263B: g_object_new (in /usr/lib/x86_64-linux-gnu/libgobject-2.0.so.0.2800.6)
==1704==    by 0x8C3BCAF: gtk_settings_get_for_screen (in /usr/lib/libgtk-x11-2.0.so.0.2400.4)
==1704==    by 0x16EE2034: ??? (in /usr/lib/gtk-2.0/modules/libcanberra-gtk-module.so)
==1704==    by 0x16EE3BEB: gtk_module_init (in /usr/lib/gtk-2.0/modules/libcanberra-gtk-module.so)
==1704==    by 0x8BE8F80: ??? (in /usr/lib/libgtk-x11-2.0.so.0.2400.4)
==1704== 
==1704== Use of uninitialised value of size 8
==1704==    at 0x7A59208: __GI___strcasecmp_l (strcmp.S:2258)
==1704==    by 0x79F0F60: __gconv_open (gconv_open.c:70)
==1704==    by 0x79FF106: _nl_find_msg (dcigettext.c:990)
==1704==    by 0x79FF818: __dcigettext (dcigettext.c:654)
==1704==    by 0x8C3D29A: ??? (in /usr/lib/libgtk-x11-2.0.so.0.2400.4)
==1704==    by 0x93BDEB4: g_type_class_ref (in /usr/lib/x86_64-linux-gnu/libgobject-2.0.so.0.2800.6)
==1704==    by 0x93A1DE3: g_object_newv (in /usr/lib/x86_64-linux-gnu/libgobject-2.0.so.0.2800.6)
==1704==    by 0x93A263B: g_object_new (in /usr/lib/x86_64-linux-gnu/libgobject-2.0.so.0.2800.6)
==1704==    by 0x8C3BCAF: gtk_settings_get_for_screen (in /usr/lib/libgtk-x11-2.0.so.0.2400.4)
==1704==    by 0x16EE2034: ??? (in /usr/lib/gtk-2.0/modules/libcanberra-gtk-module.so)
==1704==    by 0x16EE3BEB: gtk_module_init (in /usr/lib/gtk-2.0/modules/libcanberra-gtk-module.so)
==1704==    by 0x8BE8F80: ??? (in /usr/lib/libgtk-x11-2.0.so.0.2400.4)
==1704== 
Loading target settings...
Done
Hold the space bar to advance each frame
Press ctrl-c to end
[swscaler @ 0x17cc5170]No accelerated colorspace conversion found from yuv420p to bgr24.
==1704== Conditional jump or move depends on uninitialised value(s)
==1704==    at 0x4E5750F: Robot::MultiTarget::FindInFrame(cv::Mat&, cv::Mat*) (in /usr/local/lib/libdarwin.so)
==1704==    by 0x402BDB: main (main.cpp:127)
==1704== 
==1704== Conditional jump or move depends on uninitialised value(s)
==1704==    at 0x4E575E7: Robot::MultiTarget::FindInFrame(cv::Mat&, cv::Mat*) (in /usr/local/lib/libdarwin.so)
==1704==    by 0x402BDB: main (main.cpp:127)
==1704== 
0
1
1
1
==1704== Conditional jump or move depends on uninitialised value(s)
==1704==    at 0x72B6403: std::ostreambuf_iterator<char, std::char_traits<char> > std::num_put<char, std::ostreambuf_iterator<char, std::char_traits<char> > >::_M_insert_int<long>(std::ostreambuf_iterator<char, std::char_traits<char> >, std::ios_base&, char, long) const (in /usr/lib/x86_64-linux-gnu/libstdc++.so.6.0.14)
==1704==    by 0x72B6725: std::num_put<char, std::ostreambuf_iterator<char, std::char_traits<char> > >::do_put(std::ostreambuf_iterator<char, std::char_traits<char> >, std::ios_base&, char, long) const (in /usr/lib/x86_64-linux-gnu/libstdc++.so.6.0.14)
==1704==    by 0x72C1CE5: std::ostream& std::ostream::_M_insert<long>(long) (in /usr/lib/x86_64-linux-gnu/libstdc++.so.6.0.14)
==1704==    by 0x4E56B99: Robot::MultiTarget::GetMaxVotes() (in /usr/local/lib/libdarwin.so)
==1704==    by 0x4E57805: Robot::MultiTarget::FindInFrame(cv::Mat&, cv::Mat*) (in /usr/local/lib/libdarwin.so)
==1704==    by 0x402BDB: main (main.cpp:127)
==1704== 
==1704== Use of uninitialised value of size 8
==1704==    at 0x72B5F13: ??? (in /usr/lib/x86_64-linux-gnu/libstdc++.so.6.0.14)
==1704==    by 0x72B6427: std::ostreambuf_iterator<char, std::char_traits<char> > std::num_put<char, std::ostreambuf_iterator<char, std::char_traits<char> > >::_M_insert_int<long>(std::ostreambuf_iterator<char, std::char_traits<char> >, std::ios_base&, char, long) const (in /usr/lib/x86_64-linux-gnu/libstdc++.so.6.0.14)
==1704==    by 0x72B6725: std::num_put<char, std::ostreambuf_iterator<char, std::char_traits<char> > >::do_put(std::ostreambuf_iterator<char, std::char_traits<char> >, std::ios_base&, char, long) const (in /usr/lib/x86_64-linux-gnu/libstdc++.so.6.0.14)
==1704==    by 0x72C1CE5: std::ostream& std::ostream::_M_insert<long>(long) (in /usr/lib/x86_64-linux-gnu/libstdc++.so.6.0.14)
==1704==    by 0x4E56B99: Robot::MultiTarget::GetMaxVotes() (in /usr/local/lib/libdarwin.so)
==1704==    by 0x4E57805: Robot::MultiTarget::FindInFrame(cv::Mat&, cv::Mat*) (in /usr/local/lib/libdarwin.so)
==1704==    by 0x402BDB: main (main.cpp:127)
==1704== 
==1704== Conditional jump or move depends on uninitialised value(s)
==1704==    at 0x72B5F1E: ??? (in /usr/lib/x86_64-linux-gnu/libstdc++.so.6.0.14)
==1704==    by 0x72B6427: std::ostreambuf_iterator<char, std::char_traits<char> > std::num_put<char, std::ostreambuf_iterator<char, std::char_traits<char> > >::_M_insert_int<long>(std::ostreambuf_iterator<char, std::char_traits<char> >, std::ios_base&, char, long) const (in /usr/lib/x86_64-linux-gnu/libstdc++.so.6.0.14)
==1704==    by 0x72B6725: std::num_put<char, std::ostreambuf_iterator<char, std::char_traits<char> > >::do_put(std::ostreambuf_iterator<char, std::char_traits<char> >, std::ios_base&, char, long) const (in /usr/lib/x86_64-linux-gnu/libstdc++.so.6.0.14)
==1704==    by 0x72C1CE5: std::ostream& std::ostream::_M_insert<long>(long) (in /usr/lib/x86_64-linux-gnu/libstdc++.so.6.0.14)
==1704==    by 0x4E56B99: Robot::MultiTarget::GetMaxVotes() (in /usr/local/lib/libdarwin.so)
==1704==    by 0x4E57805: Robot::MultiTarget::FindInFrame(cv::Mat&, cv::Mat*) (in /usr/local/lib/libdarwin.so)
==1704==    by 0x402BDB: main (main.cpp:127)
==1704== 
==1704== Conditional jump or move depends on uninitialised value(s)
==1704==    at 0x72B6457: std::ostreambuf_iterator<char, std::char_traits<char> > std::num_put<char, std::ostreambuf_iterator<char, std::char_traits<char> > >::_M_insert_int<long>(std::ostreambuf_iterator<char, std::char_traits<char> >, std::ios_base&, char, long) const (in /usr/lib/x86_64-linux-gnu/libstdc++.so.6.0.14)
==1704==    by 0x72B6725: std::num_put<char, std::ostreambuf_iterator<char, std::char_traits<char> > >::do_put(std::ostreambuf_iterator<char, std::char_traits<char> >, std::ios_base&, char, long) const (in /usr/lib/x86_64-linux-gnu/libstdc++.so.6.0.14)
==1704==    by 0x72C1CE5: std::ostream& std::ostream::_M_insert<long>(long) (in /usr/lib/x86_64-linux-gnu/libstdc++.so.6.0.14)
==1704==    by 0x4E56B99: Robot::MultiTarget::GetMaxVotes() (in /usr/local/lib/libdarwin.so)
==1704==    by 0x4E57805: Robot::MultiTarget::FindInFrame(cv::Mat&, cv::Mat*) (in /usr/local/lib/libdarwin.so)
==1704==    by 0x402BDB: main (main.cpp:127)
==1704== 
1
==1704== Conditional jump or move depends on uninitialised value(s)
==1704==    at 0x72B6403: std::ostreambuf_iterator<char, std::char_traits<char> > std::num_put<char, std::ostreambuf_iterator<char, std::char_traits<char> > >::_M_insert_int<long>(std::ostreambuf_iterator<char, std::char_traits<char> >, std::ios_base&, char, long) const (in /usr/lib/x86_64-linux-gnu/libstdc++.so.6.0.14)
==1704==    by 0x72B6725: std::num_put<char, std::ostreambuf_iterator<char, std::char_traits<char> > >::do_put(std::ostreambuf_iterator<char, std::char_traits<char> >, std::ios_base&, char, long) const (in /usr/lib/x86_64-linux-gnu/libstdc++.so.6.0.14)
==1704==    by 0x72C1CE5: std::ostream& std::ostream::_M_insert<long>(long) (in /usr/lib/x86_64-linux-gnu/libstdc++.so.6.0.14)
==1704==    by 0x4E56BED: Robot::MultiTarget::GetMaxVotes() (in /usr/local/lib/libdarwin.so)
==1704==    by 0x4E57805: Robot::MultiTarget::FindInFrame(cv::Mat&, cv::Mat*) (in /usr/local/lib/libdarwin.so)
==1704==    by 0x402BDB: main (main.cpp:127)
==1704== 
==1704== Conditional jump or move depends on uninitialised value(s)
==1704==    at 0x72B6457: std::ostreambuf_iterator<char, std::char_traits<char> > std::num_put<char, std::ostreambuf_iterator<char, std::char_traits<char> > >::_M_insert_int<long>(std::ostreambuf_iterator<char, std::char_traits<char> >, std::ios_base&, char, long) const (in /usr/lib/x86_64-linux-gnu/libstdc++.so.6.0.14)
==1704==    by 0x72B6725: std::num_put<char, std::ostreambuf_iterator<char, std::char_traits<char> > >::do_put(std::ostreambuf_iterator<char, std::char_traits<char> >, std::ios_base&, char, long) const (in /usr/lib/x86_64-linux-gnu/libstdc++.so.6.0.14)
==1704==    by 0x72C1CE5: std::ostream& std::ostream::_M_insert<long>(long) (in /usr/lib/x86_64-linux-gnu/libstdc++.so.6.0.14)
==1704==    by 0x4E56BED: Robot::MultiTarget::GetMaxVotes() (in /usr/local/lib/libdarwin.so)
==1704==    by 0x4E57805: Robot::MultiTarget::FindInFrame(cv::Mat&, cv::Mat*) (in /usr/local/lib/libdarwin.so)
==1704==    by 0x402BDB: main (main.cpp:127)
==1704== 
1
1

==1704== Conditional jump or move depends on uninitialised value(s)
==1704==    at 0x4E57813: Robot::MultiTarget::FindInFrame(cv::Mat&, cv::Mat*) (in /usr/local/lib/libdarwin.so)
==1704==    by 0x402BDB: main (main.cpp:127)
==1704== 
0
1
1
1
1
1
1

0
1
1
1
1
1
1

0
1
1
1
1
1
1

0
1
1
1
1
1
1

0
1
1
1
1
1
1

0
1
1
1
1
1
1

0
1
1
1
1
1
1

0
1
1
1
1
1
1

Walls 3 targets:
	1 Ctr: (110,19)  Size: 31 x 70  Fill: 0.861751  Colour: 112 152 120
	2 Ctr: (114,212)  Size: 25 x 51  Fill: 0.560784  Colour: 120 155 120
	3 Ctr: (137,296)  Size: 47 x 71  Fill: 0.603236  Colour: 113 155 117

==1704== Conditional jump or move depends on uninitialised value(s)
==1704==    at 0x4E583B5: Robot::Target::FindInFrame(cv::Mat&, cv::Mat*) (in /usr/local/lib/libdarwin.so)
==1704==    by 0x402C1B: main (main.cpp:133)
==1704== 
==1704== Conditional jump or move depends on uninitialised value(s)
==1704==    at 0x4E583D3: Robot::Target::FindInFrame(cv::Mat&, cv::Mat*) (in /usr/local/lib/libdarwin.so)
==1704==    by 0x402C1B: main (main.cpp:133)
==1704== 
==1704== Conditional jump or move depends on uninitialised value(s)
==1704==    at 0x4E584F7: Robot::Target::FindInFrame(cv::Mat&, cv::Mat*) (in /usr/local/lib/libdarwin.so)
==1704==    by 0x402C1B: main (main.cpp:133)
==1704== 

```

The "Conditional jump or move depends on initialised value(s)" errors are not entirely unexpected; I didn't remember to explicitly initialise those bool variables in the constructor.  They should get set when I load settings from the .ini file.  But initialised or no they should still resolve to either 0x00 (false) or !0x00 (true), and give me 0 or 1.

The *really* weird thing is that when I run with ValGrind the error actually goes away.  See this part of the output from above:

```
0
1
1
1
1
1
1
```


as compared to the same portion of output when I run "$ ./scanline"

```
0
1
1
1
254
126
1
```

This is really a head-scratcher.  I think it must be a compiler optimization issue.  I'll get working on that theory after dinner.

Just to see if this is an issue unique to my system or not I have created an archive with the compiled binaries.  As I've said, I wish I could provide the source, but I am simply not comfortable with that as this is for our humanoid robotics team at school, and we use this code in competitions against other universities.  I understand completely if you do not want to download and run my binaries, since you have no assurances other than my word that they contain nothing malicious.  But if you are willing to give it a try and see if you can reproduce my errors you can download the program from [here](http://redstonegate.no-ip.org:65080/~minecraftsrv/weird_code.tar.bz2).

The binaries are compiled for x86_64.  The executable is in project/scanline.  The video to process is in data/video.  lib/libdarwin.so is the shared library that actually contains the buggy code.  Other libraries needed are: libcv and libhighgui.

I'll try recompiling without optimizations after dinner or sometime tomorrow and post the results.

---

### Post by trent.josephsen on 2012-01-29
This is almost certainly *not* an optimization issue; it almost certainly *is* undefined behavior you have somehow invoked elsewhere in your code; and even if the particular behavior you are seeing is unique to the specific system you're running it on (quite possible), it's even more likely that other systems will do other and possibly even more bizarre things.  That's what "undefined" means.

To clarify:  The code you first posted is not "buggy"; there's nothing wrong with it (as far as I can see); there's a bug **somewhere else** that is causing your perfectly good code to yield the wrong result.  The problem with changing your perfectly good code to avoid the issue is that the **original** bug is **still out there**, and it can still cause problems in any other, also perfectly good, code you write.

There are basically two possible sources for this underlying bug:
(1) it's somewhere else in your code (the shared library or the program that uses it); or
(2) it's in the compiler.

I'm sure it goes without saying that (1) is many orders of magnitude more likely than (2); however, if compiling without optimizations solves it and you can't find the real bug, you might be willing to chalk it up to a compiler bug -- I wouldn't want to do that until my code had been under a pretty serious regimen of scrutiny.

If I had to guess, I'd say you're probably overwriting memory you don't properly own, but in a very subtle way.  Just pulling a hypothetical out of a dark place, let's suppose that in some specific case the result of the expression (vRangeDisabled ? 0:1) gets stuffed into a memory location.  The compiler might observe that there's a memory location not currently being used for anything and use that.  But it might also observe that the same memory location "should" always contain a 1 when this code is executed (I'm stretching a little here, bear with me).  So if the memory location already contains 1, you can save time by not going out to main memory to write over it in that case.

But wait!  Suppose that memory location is just off the end of an array you're using elsewhere.  (You see where this is going now, right?)  Further suppose that somewhere along the line you have an off-by-one error, and you're writing to the memory location that should always be 1.  The compiler doesn't know this, because it's designed to make its assumptions based on the idea that you know what you're doing.  But that means the compiler actually lets you write to the memory location you asked for, and... hey presto!  126!

I'm oversimplifying, of course, but that is the kind of situation in which this kind of bug could manifest itself in the way you're observing.

---

### Post by dazman19 on 2012-01-30
shove it into an int,

and then debug that int, just before the return. See what it is.. 

Perhaps you have written to a piece of memory on the heap somewhere and done something odd. It does sound like a bug in your program. I have tear'd my hair out at strange behaviour before and nearly every single time I have found out why it was happening. 

Its worth finding out you will probably learn something.. But my advise is get a good debugger.. (some C++ debuggers are not very good).

---

### Post by muteXe on 2012-01-30
'fillDisabled' is the 2nd variable you print out. You said it worked when you used valgrind, but i see it's a 1. How can this be when you have 0 or 3 condition in your code?

edit: also, even though it's allowed, adding the results of 2 or more booleans smells of wrongness to me.

---

### Post by trent.josephsen on 2012-01-30
> **muteXe said:**
> 'fillDisabled' is the 2nd variable you print out. You said it worked when you used valgrind, but i see it's a 1. How can this be when you have 0 or 3 condition in your code?

edit: also, even though it's allowed, adding the results of 2 or more booleans smells of wrongness to me.
The 0 : 3 condition was only in the value returned -- the code that prints it uses 0 : 1

---

### Post by muteXe on 2012-01-30
ah yes :) Apologies to you.

---

