---
title: "[c++] undefined reference to..."
date: 2011-10-08
forum: Programming Talk
---

### Post by SledgeHammer_999 on 2011-10-08
I am getting a weird error while linking and I don't know how to solve it. ATM I cannot share the full source code but here are some snippets:

From CalcData.h
[php]
class CalcData
{
	private:
	static const double mp4OverheadWithBframes = 10.4;
	static const double mp4OverheadWithoutBframes = 4.3;
        ....
        private:
        void CalcVideoOverhead();
        ....
};
[/php]

From CalcData.cpp
[php]
void CalcData::CalcVideoOverhead()
{
	set_video_overhead_ratio(1.0);

    if (get_container_type() == MP4)
    {
		double temp = 1024.0 * (get_has_bframes() ? mp4OverheadWithBframes : mp4OverheadWithoutBframes) * (double)get_frames();		
		set_video_overhead(boost::math::lround(temp));
		
	}
....
}
[/php]

When I compile with g++ and it reaches the linking phase, it quits with these messages:
> ccc94zOE.o:CalcData.cpp:(.text+0xe87): undefined reference to `CalcData::mp4OverheadWithBframes'
ccc94zOE.o:CalcData.cpp:(.text+0xe9a): undefined reference to `CalcData::mp4OverheadWithoutBframes'
collect2: ld returned 1 exit status

My only use of those 2 variables is the function above. What does this error mean?

---

### Post by muteXe on 2011-10-08
As a quick test, what happens if you remove the static keywords?

---

### Post by SledgeHammer_999 on 2011-10-08
It works if remove the static keyword and initialize them in the constructor...

But I don't get it. I am able to compile and link an example class with private static const variables....

---

### Post by muteXe on 2011-10-08
declare as you have done, but dont assign values to them in the class definition, do that in your cpp file, kind of globally (ish).

edit: see [http://www.learncpp.com/cpp-tutorial/811-static-member-variables/](http://www.learncpp.com/cpp-tutorial/811-static-member-variables/), the small section called "Initializing static member variables".

---

### Post by SledgeHammer_999 on 2011-10-08
I accidentally found the solution.

In CalcData.h
[php]
class CalcData
{
    private:
    static const double mp4OverheadWithBframes;
    static const double mp4OverheadWithoutBframes;
        ....
        private:
        void CalcVideoOverhead();
        ....
}; 
[/php]

In CalcData.cpp
[php]
const double CalcData::mp4OverheadWithBframes = 10.4;
const double CalcData::mp4OverheadWithoutBframes = 4.3;
[/php]

It works but now I am even more confused because in CalcData.h right below mp4OverheadWithoutBframes I have this:

[php]
class CalcData
{
    private:
    static const double mp4OverheadWithBframes;
    static const double mp4OverheadWithoutBframes;
    static const double aviVideoOverhead = 24.0;
        ....
        private:
        void CalcVideoOverhead();
        ....
}; 
[/php]

g++/linker doesn't complain about **aviVideoOverhead** (and some other static const doubles)... Seriously wtf?

EDIT: You beat me to it. But still I don't get this behavior for **aviVideoOverhead**

---

### Post by muteXe on 2011-10-08
i'm guessing you aren't calling aviVideoOverhead in your cpp *yet*?  If you do you'll get another linking error.

---

### Post by SledgeHammer_999 on 2011-10-08
No it is also used somewhere else in the cpp.

---

