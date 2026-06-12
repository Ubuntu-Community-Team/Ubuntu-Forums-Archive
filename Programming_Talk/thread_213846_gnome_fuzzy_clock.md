---
title: "gnome fuzzy clock"
date: 2006-07-11
forum: Programming Talk
---

### Post by tich on 2006-07-11
so i've been searching everywhere for a fuzzy clock to put in the gnome panel and low and behold one doesn't exist yet.

i emailed some folks that maintain the gnome-panel-clock and they told me that the best option would be to write a patch (using the fuzzy clock for kde) and then send them a copy.

and i'm all for it!

...but i couldn't program my way out of a wet paper bag.


i, for my part, will do anything (related to making the fuzzy clock) that i am directed to do and then report back the results only to patiently await the next direction.

i could be the egor to your frankenstien and the monster would be all fuzzy.

so given that i am a ready to do the work but entirely unable to even approach the first step, is anyone willing to help me write this patch?

---

### Post by fluffington on 2006-07-12
It looks like somebody hacked one together in C# and Mono in [this thread](http://ubuntuforums.org/showthread.php?t=8108). You might want to take a look.

---

### Post by caecusum on 2007-02-16
Rather than start a brand new thread I though I might bring this one back and wipe off some dust.  I don't suppose anyone has any recent information about a Gnome fuzzy clock option?  It still gives me warm, fuzzy (harhar) feelings reminiscing about it during my KDE days.

I'm not sure what the pieced together mono hack was, but it seems a little out of my scope anyway.

Couldn't somebody with some knowhow throw something like this together pretty easily?  Pretty please? \\:D/

---

### Post by Tomosaur on 2007-02-16
Meh, I'll give it a go, but don't hold me to my word! I've got a lot of deadlines and such, and am currently forced to use Windows :(

---

### Post by caecusum on 2007-02-16
I'll be waiting patiently[-o<

---

### Post by supirman on 2007-02-20
I looked into this yesterday.  

The bad part is I've never done any gnome programming and, unfortunately, all of this gtk crap looks horribly ugly to me.  

The good part is that creating this applet should be easy.  I'll have a bit of free time this weekend, probably Saturday morning, so I'll whip something up for you.

---

### Post by supirman on 2007-02-20
A little FYI: I've talked with the gnome-panel maintainer and it seems as though I'm going to just modify the existing clock applet to do the fuzzy feature.  The only part that will take some time is internationalization.  I'm hopefully going to start on it this weekend.

---

### Post by tich on 2007-12-10
> **supirman said:**
> A little FYI: I've talked with the gnome-panel maintainer and it seems as though I'm going to just modify the existing clock applet to do the fuzzy feature.  The only part that will take some time is internationalization.  I'm hopefully going to start on it this weekend.

well i think it is my turn to wipe the dust off and bring this thread to a full circle 

--is anyone still (planning or) working on a gnome panel fuzzy clock? 
cause i am still really excited about the possibility!!

---

### Post by supirman on 2007-12-10
I never found the time/motivation to work on it, so I doubt anybody is currently doing so.  The KDE clock already does this, so you could look into their code to see how they do it.

Have fun!

---

### Post by tich on 2007-12-19
> **tich said:**
> 

i emailed some folks that maintain the gnome-panel-clock and they told me that the best option would be to write a patch (using the fuzzy clock for kde) and then send them a copy.

and i'm all for it!

...but i couldn't program my way out of a wet paper bag.




i would love to be able to look over the kde fuzzy clock code and write something for the gnome panel but even a year later (or however long it has been) i still couldn't hack my way out of a wet paper bag.

is there anyone out there that loves the idea of fuzzy time and gnome as much as i do (and is more competent than me at reading/writing code)? 

this is your chance to shine!!

---

### Post by octopuskevin on 2008-01-08
omg its the only thing of KDE that I miss... well a couple other things as well :D

I couldn't hack my way out of a box, so I too am patiently awaiting some lovely person to make this magic happen. 


Being a university student, I find the seconds and minutes feature of time keeping quite distracting and useless. I only need to know that its a quarter to 4 or that it's the evening. In a nutshell fuzzy time is my kind of time!

---

### Post by hotdoog on 2008-02-20
I would like to concur with the previous two people who would like to see this happen but do not have the means yet.

When I first tried out linux, it happened to be Knoppix and KDE. The most memorable thing to me then - at that point a naive windoze only fella - was the fuzzy clock. I still want that clock!!! It is astounding how easy this should be and yet it has yet to happen.

There is also a Gdesklet gnome version but that is also not what we want.

Maybe the 3 of us non-coders could collaberatively put it together? Does anybody know where to start? (for a non-programmer)

My only experience programming is hacking together shell script files that do basic things and crontab. Also I played with this python tutorial once.

My first guess would be that we should get the source code of the package with the gnome clock and the source code of the package with the KDE fuzzy clock and then compare them.

But, I don't know how to do that. Isn't source code accessible in a repository somewhere? Anyone able to enlighten us with the basic steps to take? Also maybe suggesting what kind of program would be used to edit/view that code?

---

### Post by pedro_orange on 2008-02-20
```
sudo apt-get source $packagename
```

Just use a text editor to read the source. You may need to install build-essential to compile it ^^

---

### Post by enigma59 on 2008-03-02
no guarantees but 

I want a fuzzy clock
I can program (C/C++)
and I've built gnome-panel before (which contains the clock applet)

---

### Post by octopuskevin on 2008-04-04
i put a post up on brainstorm.ubuntu.com about this so that maybe someone with a bit of coding skills can make this happen

---

### Post by quixote_arg on 2009-02-17
I was looking for a fuzzy clock for gnome myself, didn't find any (didn't find the kde source either) so I made one

It's extremely minimalistic, maybe too much simple, and it's in spanish (you can change it to your language easily by editing the python code).

I'm not exactly sure of the requirements... most likely python-gnome2

---

### Post by mascdman on 2009-08-28
I've posted a link on the brainstorm page to a patch for gnome-panel that adds a fuzzy clock.

---

### Post by QwUo173Hy on 2010-08-18
Hello Fuzzy People :) 

Well, a bug was reported on this issue here: [https://bugs.launchpad.net/ubuntu/+source/gnome-panel/+bug/433808]("https://bugs.launchpad.net/ubuntu/+source/gnome-panel/+bug/433808")

This was referred upstream instead, to here [https://bugzilla.gnome.org/show_bug.cgi?id=582857]("https://bugzilla.gnome.org/show_bug.cgi?id=582857")

And the reporter also mentioned the brainstorm here [http://brainstorm.ubuntu.com/idea/6252/]("http://brainstorm.ubuntu.com/idea/6252/") but was closed by the moderator because it is apparently, a bug report and not a brainstorm.

Somebody started one here [http://code.google.com/p/fuzzy-clock/]("http://code.google.com/p/fuzzy-clock/") but it hasn't been active for a while.

Not looking too good for our cause :/

---

### Post by pseudo endeavor on 2010-10-01
I will make one out of C. 

/* Stumbled upon this post looking for a fuzzy before I made the KDE > GNOME switch. */

//I love KDE. Just want to make my life interesting.

//Yes the comment blocks are funny.

---

### Post by QwUo173Hy on 2010-10-01
> **pseudo endeavor said:**
> I will make one out of C.
Really? That would be fantastic.

Put as many comments as you like :)

---

### Post by youarefunny on 2011-01-21
I programed it in C but it is not properly integrated.  I pretty much ripped out the old code and slapped in my Fuzzy code.  It works great but the settings can not be updated from the GUI.  Hopefully someone who knows the code better can properly integrate it for me.

Here is my new format_time function in 'gnome-panel-[2.32.0.2/applets/clock/clock.c]("http://2.32.0.2/applets/clock/clock.c")': (the old code is commented out)

```
static char *
format_time (ClockData *cd)
{
    struct tm *tm;
    char hour[256];
    char *utf8;

    utf8 = NULL;

    tm = localtime (&cd->current_time);

    /*if (cd->format == CLOCK_FORMAT_UNIX) {
        if (use_two_line_format (cd)) {
            utf8 = g_strdup_printf ("%lu\n%05lu",
                        (unsigned long)(cd->current_time / 100000L),
                        (unsigned long)(cd->current_time % 100000L));
        } else {
            utf8 = g_strdup_printf ("%lu",
                        (unsigned long)cd->current_time);
        }
    } else if (cd->format == CLOCK_FORMAT_INTERNET) {
        float itime = get_itime (cd->current_time);
        if (cd->showseconds)
            utf8 = g_strdup_printf ("@%3.2f", itime);
        else
            utf8 = g_strdup_printf ("@%3d", (unsigned int) itime);
    } else if (cd->format == CLOCK_FORMAT_CUSTOM) {
        char *timeformat = g_locale_from_utf8 (cd->custom_format, -1,
                               NULL, NULL, NULL);
        if (!timeformat)
            strcpy (hour, "???");
        else if (strftime (hour, sizeof (hour), timeformat, tm) <= 0)
            strcpy (hour, "???");
        g_free (timeformat);

        utf8 = g_locale_to_utf8 (hour, -1, NULL, NULL, NULL);
    } else {
        if (strftime (hour, sizeof (hour), cd->timeformat, tm) <= 0)
            strcpy (hour, "???");

        utf8 = g_locale_to_utf8 (hour, -1, NULL, NULL, NULL);
        }*/
        
       
#define FUZZY_5MIN 0
#define FUZZY_10MIN 1
#define FUZZY_15MIN 2
#define FUZZY_30MIN 3
#define FUZZY_60MIN 4
#define FUZZY_TODP 5     //      Time of Day Percise
#define FUZZY_TOD 6      //      Time of Day
#define FUZZY_DOW 7      //      Day of Week
#define FUZZY_TOW 8      //      Time of Week
        
        unsigned int percision = FUZZY_15MIN;
        
        static char time_strings[][25] = {    "%s O'Clock",           // 0
                                                "Five after %s",
                                                "Ten after %s",
                                                "Quarter after %s",
                                                "Twenty after %s",
                                                "Twenty-Five after %s",
                                                "Half past %s",
                                                "Thirty-five after %s",
                                                "Twenty to %s",         // 8
                                                "Quarter to %s",
                                                "Ten to %s",
                                                "Five to %s",
                                                "Early Morning",        // 12
                                                "Morning",
                                                "Afternoon",
                                                "Late Afternoon",
                                                "Evening",
                                                "Night",
                                                "Weekday",              // 18
                                                "Weekend",
                                           };
        
        static char hour_names[][10] = {
                                                "Twelve",
                                                "One",
                                                "Two",
                                                "Three",
                                                "Four",
                                                "Five",
                                                "Six",
                                                "Seven",
                                                "Eight",
                                                "Nine",
                                                "Ten",
                                                "Eleven"
                                        };
        
        static char day_names[][10] =   {
                                                "Sunday",
                                                "Monday",
                                                "Tuesday",
                                                "Wednesday",
                                                "Thursday",
                                                "Friday",
                                                "Saturday"
                                        };
        
        struct tm *time;
        time = localtime(&cd->current_time);
        
        int cur_hour = time->tm_hour;
        if ( cur_hour >= 12 ) cur_hour -= 12;
        
        if ( percision == FUZZY_5MIN )
        {                
                if ( time->tm_min >= 58 )       
                {
                        cur_hour++;
                        sprintf(hour, time_strings[0], hour_names[cur_hour]);
                }
                else
                {
                        if ( time->tm_min > 37 )        cur_hour++;     //      If we are saying "to something"
                        sprintf(hour, time_strings[(time->tm_min+2)/5], hour_names[cur_hour]);
                }
        }
        else if ( percision == FUZZY_10MIN )
        {                
               if ( time->tm_min >= 55 )       
                {
                        cur_hour++;
                        sprintf(hour, time_strings[0], hour_names[cur_hour]);
                }
                else
                {
                        if ( time->tm_min >= 35  )        cur_hour++;     //      If we are saying "to something"
                        sprintf(hour, time_strings[((time->tm_min+5)/10)*2], hour_names[cur_hour]);
                }
        }
        else if ( percision == FUZZY_15MIN )
        {       
                if ( time->tm_min >= 53 )       
                {
                        cur_hour++;
                        sprintf(hour, time_strings[0], hour_names[cur_hour]);
                }
                else
                {
                        if ( time->tm_min > 37 )        cur_hour++;     //      If we are saying "to something"
                        sprintf(hour, time_strings[((time->tm_min+7)/15)*3], hour_names[cur_hour]);
                }
        }
        else if ( percision == FUZZY_30MIN )
        {
                if ( time->tm_min >= 58 )       
                {
                        cur_hour++;
                        sprintf(hour, time_strings[0], hour_names[cur_hour]);
                }
                else
                {
                        if ( time->tm_min >= 45 )        cur_hour++;     //      If we are saying "to something"        
                        sprintf(hour, time_strings[((time->tm_min+15)/30)*6], hour_names[cur_hour]);
                }
        }
        else if ( percision == FUZZY_60MIN )
        {                
                if ( time->tm_min >= 30 )       cur_hour++;     //      Round up
                
                sprintf(hour, time_strings[0], hour_names[cur_hour]);
        }
        else if ( percision == FUZZY_TODP )
        {                
                strcpy(hour, time_strings[(time->tm_hour/4)+12]);
        }
        else if ( percision == FUZZY_TOD )
        {                
                strcpy(hour, time_strings[((time->tm_hour/8)*2)+12]);
        }
        else if ( percision == FUZZY_DOW )
        {                
                strcpy(hour, day_names[time->tm_wday]);
        }
        else if ( percision == FUZZY_TOW )
        {                
                if (( time->tm_wday == 0 ) || ( time->tm_wday == 6 ))    strcpy(hour, time_strings[19]);
                else    strcpy(hour, time_strings[18]);
        }
        
        
        utf8 = g_locale_to_utf8 (hour, -1, NULL, NULL, NULL);
    if (!utf8)
        utf8 = g_strdup (hour);

        return utf8;
}
```to change the level of fuzziness just change the value of precision.


To compile it download the gnome-panel source and update the one function.  Enjoy your fuzziness.  I wrote this in two days so please tell me about any bugs.

---

### Post by bonesTdog on 2011-01-31
Here is a link to a fuzzy Clock that someone developed.  It is working swimmingly for me.  My life is whole again with Fuzzy Clock!
[http://brainstorm.ubuntu.com/idea/6252](http://brainstorm.ubuntu.com/idea/6252)

---

