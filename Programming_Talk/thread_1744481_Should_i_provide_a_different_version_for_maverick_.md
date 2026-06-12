---
title: "Should i provide a different version for maverick and natty?"
date: 2011-04-30
forum: Programming Talk
---

### Post by leon.vitanos on 2011-04-30
So i have an application that i have created a deb package which can be installed in both Ubuntu 10.10 and 11.04 with no problems. The only reason why i am thinking of providing a different version for maverick and natty is because in Unity the menubar is been shown on the panel and not in the window, because my app has standard width and height ( it cannot be maximized ) and because of that there is a space on the bottom of the window and it is a big ugly now( If u didn't understand what i said i can take some screenshots ) 

But this is only in Unity.. If you switch to Ubuntu Classic ( Gnome ), the menubar will be on the window and not in the panel.. 

So should i provide a version for ubuntu 10.10 ( including ubunu 11.04, ubuntu classic ) and one for the unity or keep one version for both 10.10 and 11.04 but considering that at unity the app will be a bit ugly? :-k

---

### Post by hakermania on 2011-04-30
The application is 'wallch' which you can find in my signature as well.
Another problem is that now you cannot access the tray(when an application is minimized to tray). Only the indicators are shown :(

---

### Post by wmcbrine on 2011-04-30
Maybe you could detect the environment and change behavior accordingly? I don't know how, but there's surely a way...

---

### Post by WitchCraft on 2011-05-01
Execute popen on lsb_release -c

This outputs:
> 
Codename:	maverick


Then you do sscanf on "Codename:	<whatever>"

Like this:
```

#ifdef __cplusplus 
    #include <cstdio>
    #include <cstdlib>
    #include <cstring>
#else
    #include <stdio.h>
    #include <stdlib.h>
    #include <string.h>
#endif


int main(int argc, char* argv[])
{
    char szRelease [100];


    FILE* pPipe  = popen("lsb_release -c", "r");
    char   psBuffer[256];
    while( !feof( pPipe ) )
    {
        fgets( psBuffer, 256, pPipe );
    }

    pclose(pPipe);
    printf("String: %s\n", psBuffer);
    sscanf(psBuffer, "Codename: %s", szRelease);
    printf("Ubuntu Version: \"%s\"\n", szRelease);
    return EXIT_SUCCESS;
}

```


Which you can finalize like this:
```

#ifdef __cplusplus 
    #include <cstdio>
    #include <cstdlib>
    #include <cstring>
#else
    #include <stdio.h>
    #include <stdlib.h>
    #include <string.h>
#endif



static char* getUbuntuVersion()
{
    static char szRelease[100];   
    char psBuffer[256];
    
    if(szRelease[0] != 0)
        return szRelease;
    
    FILE* pPipe  = popen("lsb_release -c", "r");
    
    while( !feof( pPipe ) )
    {
        fgets( psBuffer, 256, pPipe );
    }
    pclose(pPipe);	
    
    
    //printf("String: %s\n", psBuffer);
    
    sscanf(psBuffer, "Codename: %s", szRelease);
    
    //printf("Ubuntu Version: \"%s\"\n", szRelease);
    return szRelease;
}



static float getUbuntuVersionNumber()
{
    static float fRelease = 0.0f;
    char psBuffer[256];
    
    if(fRelease != 0.0f)
        return fRelease;
    
    FILE* pPipe  = popen("lsb_release -r", "r");
    
    while( !feof( pPipe ) )
    {
        fgets( psBuffer, 256, pPipe );
    }
    pclose(pPipe);	
    
    //printf("String: %s\n", psBuffer);
    
    sscanf(psBuffer, "Release: %f", &fRelease);
    
    //printf("Ubuntu Release: \"%f\"\n", fRelease);
    return fRelease;
}


int isThisThisUbuntuVersion(const char* szVersionInQuestion)
{
	char* szUbuntuVersion = getUbuntuVersion();
	return !strcasecmp(szUbuntuVersion, szVersionInQuestion);
}


int main(int argc, char* argv[])
{
    printf("Ubuntu Version: %5.2f\n\n", getUbuntuVersionNumber());
    
    if(isThisThisUbuntuVersion("maverick"))
        printf("Yes\n");
    else
        printf("No\n");
    
    
    if(isThisThisUbuntuVersion("natty"))
        printf("Yes\n");
    else
        printf("No\n");
    
    
    return EXIT_SUCCESS;
}


```


> 
Ubuntu Version: 10.10

Yes
No


---

### Post by MadCow108 on 2011-05-01
> **WitchCraft said:**
> Execute popen on lsb_release -c

no need for popen. just read
/etc/lsb-release
(or source it before execution)

---

### Post by wmcbrine on 2011-05-01
Yeah but you don't want to base it on the release, you want to base it on Classic vs. Unity.

---

### Post by WitchCraft on 2011-05-07
Try this:


cat /proc/self/environ


Ubuntu 10.10 with Gnome:
> 
XDG_CONFIG_DIRS=/etc/xdg/xdg-gnome:/etc/xdg
PATH=/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games
USER=root
SSH_AUTH_SOCK=/tmp/keyring-Iwx6wc/ssh
SHELL=/bin/bash
DBUS_SESSION_BUS_ADDRESS=unix:abstract=/tmp/dbus-1j5alk9pIZ,guid=a6e22e5e7b52251e9b28237e00000108
GDM_LANG=en_US.UTF-8
GTK_MODULES=canberra-gtk-module
GNOME_KEYRING_PID=1632
MANDATORY_PATH=/usr/share/gconf/gnome.mandatory.path
XDG_SESSION_COOKIE=36656152cb44593c562ae00000000007-1304793661.9359-CENSORED
GDMSESSION=gnome
LANG=en_US.UTF-8
WINDOWPATH=7
GNOME_KEYRING_CONTROL=/tmp/keyring-Iwx6wc
WINDOWID=73402660
USERNAME=root
COLORTERM=gnome-terminal
TERM=xterm
PWD=/root
ORBIT_SOCKETDIR=/tmp/orbit-root
GNOME_DESKTOP_SESSION_ID=this-is-deprecated
GDM_KEYBOARD_LAYOUT=ch	de_nodeadkeys
SESSION_MANAGER=local/IS1300-1:@/tmp/.ICE-unix/1651,unix/IS1300-1:/tmp/.ICE-unix/1651
DISPLAY=:0.0
UBUNTU_MENUPROXY=libappmenu.so
LOGNAME=root
XDG_DATA_DIRS=/usr/share/gnome:/usr/local/share/:/usr/share/
DEFAULTS_PATH=/usr/share/gconf/gnome.default.path
DESKTOP_SESSION=gnome
SSH_AGENT_PID=1683
HOME=/root
XAUTHORITY=/var/run/gdm/auth-for-root-SG2r5l/database


Looks like DESKTOP_SESSION is the one value you need:
```

man 3 getenv

```

---

