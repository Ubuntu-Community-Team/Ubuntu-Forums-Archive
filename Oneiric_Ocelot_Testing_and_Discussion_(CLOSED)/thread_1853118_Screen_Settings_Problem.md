---
title: "Screen Settings Problem"
date: 2011-10-01
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by kuvanito on 2011-10-01
the screen dims too fast I say,even if I choose 1 hour,i must be constantly moving the mouse in order to watch a movie,it kicks on at any time and randomly.any one with this problem?

---

### Post by MG&amp;TL on 2011-10-01
I haven't had this problem, and I'm using 11.04 at the mo, so this might not be accurate. Can you not set it under power management not to dim the display at all?

---

### Post by sammiev on 2011-10-01
Hi, go into system settings and select screen. Make your changes there. :)

---

### Post by rtalcott on 2011-10-01
even making the selection in SCREEN it still dims almost immediately...I have the problem on 3 machines running updated 11.10

---

### Post by kuvanito on 2011-10-01
i am with rtalcott here
settings does not matter even power settings
something is wrong with screen settings and Oneiric 11.10
never or 1 hour means nothing,it will come even faster

---

### Post by rtalcott on 2011-10-01
I started seeing this a couple days ago...

---

### Post by sammiev on 2011-10-01
Read post number 3 and unckeck dim to save power. I had to do that to all my computers running 11.10 :)

---

### Post by rtalcott on 2011-10-01
There is no dim to save power setting...

---

### Post by kuvanito on 2011-10-01
once again I am with rtalcott here
people read my first post
this Oneiric here
there is no setting for dim to save power,read well b4 posting

---

### Post by c0stalkayk3r on 2011-10-01
I'm having similar problems. if I set my screen time out to 1 hour, it might turn off in 10 minutes, or 30 but never a full hour... also if I set it to "Never" dim, it dims immediately, unchecking the "Dim to save power" box has no effect on this issue. Any idea what package to file this bug under?

---

### Post by kuvanito on 2011-10-01
i have no idea but it's driving me crazy here.....
i hope it is fixed soon,after all it's a beta,hehehehe :p

---

### Post by effenberg0x0 on 2011-10-01
Hey,

I have posted a workaround at [http://ubuntuforums.org/showthread.php?t=1851688](http://ubuntuforums.org/showthread.php?t=1851688).
Basically, you'll run "sudo nohup ./no_sleep.sh &".
It simulates a mouse movement every n minutes, so that the screen won't dim.
I use it on my XBMC HTPC and its fine as a small workaround for now...

Regards,
Effenberg

---

### Post by kuvanito on 2011-10-01
thank you! brilliant idea for now,i am sure it will be fixed.....;)

---

### Post by xyzzyman on 2011-10-01
I have to move the mouse constantly as it instantly starts to dim until it winds up locking the screen.

---

### Post by rtalcott on 2011-10-01
very strange...2 machines...same model motherboard....using onboard graphics...AMD....installed both today (I think I did...maybe not)...one has the problem and one does not...

---

### Post by sammiev on 2011-10-01
Hmmm :p

---

### Post by xyzzyman on 2011-10-01
sammiev, even with that unchecked mine was instantly dimming when i'd stop typing or moving the mouse and woudl just keep dimming and shutting off. it was happening in unity 2d also, but not under a new user account, so even after searching every option in dconf-editor and gconf-editor, i just deleted the dconf folder and it's all fixed. had to recustomize some things but took just a few minutes.

---

### Post by rtalcott on 2011-10-01
I am not on a laptop..I have no such setting...on my hardware there is no dim setting...

---

### Post by sammiev on 2011-10-01
I am on gnome3, maybe there is a difference. I have all 3 laptops with the same settings that had the same problems a few weeks back. Please tell me if you are using gnome or other. :)

---

### Post by cariboo on 2011-10-02
> **sammiev said:**
> I am on gnome3, maybe there is a difference. I have all 3 laptops with the same settings that had the same problems a few weeks back. Please tell me if you are using gnome or other. :)

The problem is more than likely with gnome 3, so those affected will be, whether they are using gnome-shell or unity.

---

### Post by Quackers on 2011-10-02
I just ran an update for System Settings and now although there is no option to turn off the screen dimming there is an option to set it to "never", which wasn't there before, I think.
I set it to never and logged out/in and the screen didn't turn off in 15 minutes. That's an improvement at least :-)
I'm using 64 bit gnome-shell here.

---

### Post by Quackers on 2011-10-02
Nope! Sadly the screen still turns off - it just takes longer now.

---

### Post by kuvanito on 2011-10-02
I am using my desktop not a laptop
I have a clean install of Oneiric not an update from any Ver.
I run 32 bit not 64 Bit
I do not use Gnome Shell but Unity,neither have I installed it.(clean oneiric)
I do not have a setting Dim to save nothing and even thou I have selected Never for the screen it goes ON inmediatly,my best setting is for 30 Min but it comes on randomly at any given time,could take 5 min or 15 min for the Dimmed or Black Screen to kick on,I can't even watch a movie,well like I said before it's only a Beta.....

---

### Post by paul_in_london on 2011-10-02
Used 2 suggestions from this thread a while back:

[http://ubuntuforums.org/showthread.php?t=1832942&highlight=oneiric+seeker+dpms](http://ubuntuforums.org/showthread.php?t=1832942&highlight=oneiric+seeker+dpms)

In xorg.conf:

```
Section "ServerFlags"
     [B][COLOR="Red"]Option "blank time" "0"
     Option "standby time" "0"
     Option "suspend time" "0"
     Option "off time" "0"
     Option "dpms" "false"[/COLOR][/B]
     Option "IgnoreABI" "True"
EndSection
```

Second thing:

```
dconf-editor, 'org --> gnome --> desktop --> screensaver and unchecked the box next to 'idle-activation-enabled'.
```

This still seems to be working. I noticed recently that the "Never" screensaver option has finally (re-)appeared!

The latest "related" problem was that I had to disable hibernate/suspend (which I don't use anyway) by editing **/usr/share/polkit-1/actions/org.freedesktop.upower.policy** to make it look like this:

```
<?xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE policyconfig PUBLIC
 "-//freedesktop//DTD PolicyKit Policy Configuration 1.0//EN"
 "http://www.freedesktop.org/standards/PolicyKit/1.0/policyconfig.dtd">
<policyconfig>
  <vendor>The UPower Project</vendor>
  <vendor_url>http://upower.freedesktop.org/</vendor_url>
  <icon_name>system-suspend</icon_name>

  <action id="org.freedesktop.upower.suspend">
    <description>Suspend the system</description>
    <description xml:lang="fr">Mettre le système en veille</description>
    <description xml:lang="it">Sospende il sistema</description>
    <description xml:lang="pl">Wstrzymanie systemu</description>
    <description xml:lang="sv">Försätt systemet i vänteläge</description>
    <message>Authentication is required to suspend the system</message>
    <message xml:lang="fr">Vous devez vous identifier pour mettre le système en veille</message>
    <message xml:lang="it">È richiesto autenticarsi per sospendere il sistema</message>
    <message xml:lang="pl">Wymagane jest uwierzytelnienie, aby wstrzyma&#263; system</message>
    <message xml:lang="sv">Autentisering krävs för att försätta systemet i vänteläge</message>
    <defaults>
[B][COLOR="Red"]      <allow_inactive>yes</allow_inactive>
      <allow_active>no</allow_active>
[/COLOR][/B]    </defaults>
  </action>

  <action id="org.freedesktop.upower.hibernate">
    <description>Hibernate the system</description>
    <description xml:lang="fr">Mettre le système en hibernation</description>
    <description xml:lang="it">Iberna il sistema</description>
    <description xml:lang="pl">Hibernacja systemu</description>
    <description xml:lang="sv">Försätt systemet i viloläge</description>
    <message>Authentication is required to hibernate the system</message>
    <message xml:lang="fr">Vous devez vous identifier pour mettre le système en hibernation</message>
    <message xml:lang="it">È richiesto autenticarsi per ibernare il sistema</message>
    <message xml:lang="pl">Wymagane jest uwierzytelnienie, aby zahibernowa&#263; system</message>
    <message xml:lang="sv">Autentisering krävs för att försätta systemet i viloläge</message>
    <defaults>
[B][COLOR="Red"][COLOR="Red"]      <allow_inactive>yes</allow_inactive>
      <allow_active>no</allow_active>[/COLOR][/COLOR][/B]
    </defaults>
  </action>

</policyconfig>
```

(See this thread: [http://ubuntuforums.org/showthread.php?p=11301692#post11301692](http://ubuntuforums.org/showthread.php?p=11301692#post11301692))

---

### Post by Harry33 on 2011-10-02
> **Quackers said:**
> I just ran an update for System Settings and now although there is no option to turn off the screen dimming there is an option to set it to "never", which wasn't there before, I think.
I set it to never and logged out/in and the screen didn't turn off in 15 minutes. That's an improvement at least :-)
I'm using 64 bit gnome-shell here.

Which update is that?

---

### Post by Quackers on 2011-10-02
Dunno boss, it came with the last set of updates. There was a gnome-shell update and a few kde updates as well.

Ah! History is a useful thing :-) it was this one
```
systemsettings (4:4.7.1-0ubuntu4) to 4:4.7.1-0ubuntu5
```

---

### Post by Harry33 on 2011-10-02
> **Quackers said:**
> Dunno boss, it came with the last set of updates. There was a gnome-shell update and a few kde updates as well.

Ah! History is a useful thing :-) it was this one
```
systemsettings (4:4.7.1-0ubuntu4) to 4:4.7.1-0ubuntu5
```

Ah OK, I see.
Systemsettings is a KDE configurator. I only use Gnome.
That has nothing to with Gnome-shell either.

---

### Post by Quackers on 2011-10-02
Oh! Why did that arrive as an update then? I've never had KDE on here.

---

### Post by Harry33 on 2011-10-02
> **Quackers said:**
> Oh! Why did that arrive as an update then? I've never had KDE on here.

You should remove that package, purging it.

---

### Post by t1497f35 on 2011-10-02
I'm having same issues, did anyone file a bug yet? It's annoying as hell especially when watching a movie!

---

### Post by Quackers on 2011-10-02
> **Harry33 said:**
> You should remove that package, purging it.

Aha! Thanks! Consider it removed! :D
I wonder what persuaded me to install that? (If I did ;))

EDIT: Duly purged!

---

### Post by sammiev on 2011-10-02
I installed beta 2 no more than a week a go and only had to do post 3 and change the time to 1 hour and I get 1 hour between screen dims. I'm surprised at this thread as I said already, 3 laptops running all the same setups with no problems. I will follow this thread and check my settings as the post come in.

---

