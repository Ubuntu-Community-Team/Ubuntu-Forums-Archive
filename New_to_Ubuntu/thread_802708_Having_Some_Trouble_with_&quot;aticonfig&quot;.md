---
title: "Having Some Trouble with &quot;aticonfig&quot;"
date: 2008-05-21
forum: New to Ubuntu
---

### Post by =Fus3= on 2008-05-21
All right, so I just installed ATi's latest driver for my GPU (an ATI Xpress 200), did the install, and when I got to something like step 7 on their site, do aticonfig --initial for the first time, it gives me this error:

Found fglrx primary device section
Nothing to do, terminating.

Aticonfig on its own works, though:

Usage: aticonfig [OPTION] ...
Parses an existing X-Server configuration file and modifies it to operate with
ATI products.

The following command-line options can be invoked as parameters:

ATI Initial Configuration:
  --initial
        Generate a default ATI device section in the configuration file which
        is capable of loading the fglrx driver.
  --initial=dual-head
        Same as '--initial' but generate a basic dual head configuration file.
  --initial=check
        Identifies if the fglrx driver is present in configuration file.

TV Options:
  --tvf, --tv-format-type=STRING
        Change the TV signal format.  STRING can be one of:
           NTSC-M 
           NTSC-JPN
           NTSC-N
           PAL-B
           PAL-COMB-N
           PAL-D
           PAL-G
           PAL-H
           PAL-I
           PAL-K
           PAL-K1
           PAL-L
           PAL-M
           PAL-N
           PAL-SECAM-D
           PAL-SECAM-K
           PAL-SECAM-K1
           PAL-SECAM-L
        Note: Not all graphics cards support every mode. Regional 
              settings are applicable. 
  --tvs, --tv-standard-type=STRING
        Change the TV standard for TV output.  STRING can be one of:
            VIDEO
            SCART
            YUV
 --tv-overscan={on|off}
       Enable or disable overscan mode for TVout
       Note, not all tv-formats support overscan. Try to 
       toggle overscan off before changing tv-format if 
       and error occurs. 
 --tv-info
         Print out the current tv geometry, tv format, and if the
         tv is physically connected. 
 --tv-geometry=WIDTHxHEIGHT{+|-}X{+|-}Y
              =WIDTHxHEIGHT
         Change the size and position of the TVout display. 
         WIDTH and HEIGHT are in percentage units. Please note
         that the valid range for WIDTH and HEIGHT depends on
         the tv-format selected. However, as a rule of thumb  
         WIDTH and HEIGHT are valid in the range [1,100]  
         X and Y are pixels offsets from centre 
         of the screen. X and Y are have variable ranges dependant 
         on ASIC. Use tv-info to get valid X and Y ranges 
         If tv-geometry is invoked with just width and height 
         then X and Y are assumed to be 0
         See example 5 below for a sample usage. 

FireGL Workstation Board Features:
  --app, --use-app-profile=STRING
        Change the application profile for a FireGL workstation board.
        STRING can be one of:
            default
            maya
            softimage-xsi
            softimage-3d
            houdini4.0
            houdini5.0
            houdini5.5
FSAA Options:
  --fsaa={on|off}
        Enable/disable full scene anti-aliasing.  Enable this option to enhance
        photo-realism in 3D rendering.  Disable it to get the most accurate 3D
        image.
  --fs, --fsaa-samples={off,0,2,4,6}
        Set the number of FSAA samples per pixel or 2, 4, 6.  off is the same
        as setting 0 samples.
  --fsg, --fsaa-gamma={on|off}
        Enable/disable FSAA gamma.
  --fmsp, --fsaa-ms-positions=x0,y0,x1,y1,x2,y2,x3,y3,x4,y4,x5,y5
        Change the FSAA Multi-Sample Positions for x0,y0 to x5,y5.  You must
        specify exactly 12 real number values separated by commas.

Screen-Related Options:
  --ovt, --overlay-type=STRING
        Change the overlay for the X server.  STRING can be one of:
            opengl
            Xv
            disable
  --ovon, --overlay-on={0|1}
        Choose which head the hardware overlay should be visible on.  The
        hardware overlay can be used for either OpenGL, video, pseudo-color
        or stereo.
  --lcd, --lcd-mode=STRING
        Change the LCD mode.  STRING can be one of:
            center
            full
  --dtop, --desktop-setup=STRING
        Change the desktop setup for multiple display adapters.
        STRING can be one of:
            single              1 screen, second dark
            mirror              2 screens - same content, identical
                                refresh rate/resolution
                                Note: This option is NOT supported with Avivo
            clone               2 screens - same content, allows for
                                different refresh rates/resolutions
            horizontal          2 screens - one framebuffer,
                                screen 1 right of screen 0
            horizontal,reverse  2 screens - one framebuffer,
                                screen 1 left of screen 0
            vertical            2 screens - one framebuffer,
                                screen 1 above of screen 0
            vertical,reverse    2 screens - one framebuffer,
                                screen 1 below of screen 0
        Note:  This option is not valid if '--initial=dual-head' is specified.
  --vs, --sync-vsync={on|off}
        Enable/disable sync buffer swaps with vsync.  Enable this option to
        prevent tearing during 3D rendering.
  --psc, --pseudo-color={on|off}
        Enable/disable pseudo-color visuals.  Enable this option to get 16-bit
        color support.
  --stereo={on|off}
        Enable/disable quad-buffer stereo support.  Enable this option only for
        using applications that support the use of hardware 3D shutter glasses.
  --ss, --stereo-sync={on|off}
        Enable/disable quad-buffer stereo sync.  Enable this option to get 3D
        glasses to synchronize with the infrared transmitter.
  --resolution=Screen#,W1xH1,W2xH2,W3xH3,...
        Set the modes for the specified screen.  You may specify several
        resolutions separated by commas.
        Screens start at 0.  You can use 1 for dual-head
  --hsync=Screen#,LOW-HIGH
        Change the horizontal sync range of the specified monitor.  Make sure
        you know the capabilities of your monitor before changing this option.
        Screens start at 0.  You can use 1 for dual-head
  --vrefresh=Screen#,LOW-HIGH
        Change the vertical refresh range of the specified monitor.  Make sure
        you know the capabilities of your monitor before changing this option.
        Screens start at 0.  You can use 1 for dual-head
  --hsync2=LOW-HIGH
        Change the horizontal sync range of the second display.  Make sure you
        know the capabilities of your monitor before changing this option.
  --vrefresh2=LOW-HIGH
        Change the vertical refresh range of the second display.  Make sure you
        know the capabilities of your monitor before changing this option.
  --mode2=W1xH1,W2XH2,W3xH3,...
        Change the modes for the second display.  You may specify several
        resolutions separated by commas.  Only valid for clone and big desktop
        settings.
  --screen-layout={left|right|above|below}
        Set the secondary screen position for dual head.
  --screen-overlap=NUM
        Set the screen overlap region in big desktop mode to be NUM pixels.
  --force-monitor=STRING[,STRING...]
        Describe all displays that are to be enabled and/or disabled regardless
        of physical connection.  STRING can be one or more of the following
        set, separated by commas:
            crt1
            crt2
            lvds
            tv
            tmds1
            tmds2
            tmds2i
            nocrt1
            nocrt2
            nolvds
            notv
            notmds1
            notmds2
            notmds2i

POWERplay Options:
  Following options will not change the config file. 
  These options will be effective immediately. Other options on 
  the same command line will be ignored.
  --lsp, --list-powerstates
        Print information about power states and exit.
  --set-powerstate=NUMBER
        Set a power state listed by --list-powerstates.

Advanced Options:
  --sync-video={on|off}
        Enable/disable sync to vsync for AVIVO video.
        This option is enabled by default and is used to prevent
        video tearing. By disabling this option video is free to
        render as fast as the 3D engine can handle. In the case of
        choppy video try to disable sync-video.
  --tls={on|off}
        Enable/disable fast thread local storage.  Disable this option when
        virtual machines or WineX fail to work properly.
  --sb, --signal-block={on|off}
        Enable/disable signal blocking.  Disable this option when debugging a
        multi-threaded OpenGL application.
  --locked-userpages={on|off}
        Enable/disable locked user pages. Disable this option if the system
        hangs when running fgl_glxgears.
        User page lock is no longer available on AGP system now.
  --gcpu, --generic-cpu={on|off}
        Enable/disable generic CPU.  Use this option if the CPU is being
        reported improperly.  For example: If you have an AMD cpu that is
        being reported as Intel.
  --max-gart-size=NUMBER
        Set user-defined max GART size for non-AGP systems.
        Possible integer values are from 64 to 512 (mb).

Dynamic Display Management Options:
  Following options will not change the config file. They are
  used for querying driver, controller and adaptor information.
  These options will be effective immediately. Other options on 
  the same command line will be ignored.
  --enable-monitor=STRING,STRING
        Setting current monitor to be enabled. Only 2 displays
        can be enabled at the same time. Any displays
        that are not on the list will be disabled.
        STRING can be one of the following set, separated 
        by commas:
            none
            crt1
            crt2
            lvds
            tv
            tmds1
            tmds2
            auto   -- use default policy to enable the displays.
  --query-monitor
        This will return connected and enabled monitor information
  --swap-monitor
        This only works for big desktop setup. This will swap the
        contents on the two monitors.
  --swap-screens={on|off}
        Enable/disable swap heads in dual-head mode.
        This option works only in dual-head mode.

Pair mode options: 
  Following options are used for query add and remove pair modes. 
  These options will be effective immediately. Other options on   
  the same command line will be ignored.
  --list-pairmode 
        list all the current existing pair modes the driver can use.
  --add-pairmode=width0xheight0+width1xheight1
        Add one pair mode to the list. width0 and height0 are the 
        size of primary display and width1 and height1 for the 
        secondary  display.
  --remove-pairmode=index 
        Remove one pair mode from the list. User can get index by 
        list-pairmode.

External Events Daemon Options:
  Following options will not change the config file. They are
  used to send commands to the atieventsd external events daemon.
  --set-policy=STRING
        Sets the event policy for the daemon to be STRING.
        See the atieventsd(8) manpage for further details.

Display attribute options:
  Following options are used for query and set adjustment of 
  specific attribute for specific display. These options will be 
  effective immediately. Other options on the same command line 
  will be ignored.
  The DISPLAYTYPE in options can be one of the following strings:
        crt1, lvds, tv, tmds1, crt2, tmds2, cv, tmds2i .
   The ATTRIBTYPE in options can be one of the following strings:
        brightness, contrast, saturation, hue, positionX, 
        positionY, sizeX, sizeY, overscan, videoStandard  
  --query-dispattrib=DISPLAYTYPE,ATTRIBTYPE 
        query the specific adjustment info of the specific display.
        if ATTRIBTYPE is not specified, all supported attribute 
        information will be printed out. 
  --set-dispattrib=DISPLAYTYPE,ATTRIBTYPE:VALUE 
        set the attribute value of the specific display.

Connector type options:
  Following options are used for query connector type 
  for specific display. These options will be 
  effective immediately. Other options on the same command line 
  will be ignored.
  The DISPLAYTYPE in options can be one of the following strings:
        crt1, lvds, tv, tmds1, crt2, tmds2, cv, tmds2i .
   --query-connectortype=DISPLAYTYPE 
        query the connector type of the specific display.

Component video dongle options:
  Following options are used for query and set dongles for a 
  component video. These options will be effective immediately.
  Other options on the same command line will be ignored.
  --query-cvdongle
        query dongle setting informations of the component video.
  --set-cvdongle=VALUE
        set the custom override value of the CV dongle. 
  --reset-cvdongle
        reset the custom override setting(to zero)of the CV dongle.

Component video customized mode options:
  Following options are used for query and set customized mode for
  component video. These options will be effective immediately.
  Other options on the same command line will be ignored.
  --query-cvmode
        query customized modes for component video.
  --add-cvmode=WIDTH,HEIGHT,FLAGS,BASEWIDTH,BASEDHEIGHT,REFRESH.
        add a customized mode for component video.
  --validate-cvmode=WIDTH,HEIGHT,FLAGS,BASEWIDTH,BASEHEIGHT,REFRESH.
        validate a customized mode for component video.
  --delete-cvmode=INDEX 
        delete one customized mode for component video. 

Persistent Configuration Store (PCS) Options:
  Following options will not change the config file. They are
  used to manipulate the PCS database.  Due to their nature, these.
  commands may only be run by the root user. Note that the prefix
  and key names are not case-sensitive.
  --get-pcs-key=PREFIX,KEY
        Prints out the specified prefix and key from the PCS
        database.  The type of data will be shown along with
        the contents.
  --set-pcs-val=PREFIX,KEY,VALUE
        Sets an integer value at the specified prefix and key in
        the PCS database.  The value may be specified in hex by
        prefixing it with 0x or in octal by prefixing it with 0,
        otherwise the value is assumed to be in decimal.
  --set-pcs-str=PREFIX,KEY,STRING
        Sets a string value at the specified prefix and key in
        the PCS database.
  --set-pcs-raw=PREFIX,KEY,HEXSTRING
        Sets a raw binary value at the specified prefix and key in
        the PCS database.  The value is specified as a series of
        hex bytes with no 0x or spaces.
        (e.g. --set-pcs-raw="TestSection,TestData,E84C0E" sets 3 bytes)
  --del-pcs-key=PREFIX,KEY
        Deletes the specified prefix and key from the PCS database.

Miscellaneous Options:
  -v, --verbose
        Show what aticonfig is doing.
  -q, --quiet
        Disable all information output except for errors.
  --effective={now,startup}
        Choose when the requested changes should take effect.
            now:     Immediately.  This change will affect the running X
                     session if applicable.  Only 'set-powerstate' and
                     'overlay-on' are applicable for now.
            startup: On future X server startups.  This change will modify the
                     X server configuration file if applicable.
        The default is 'now,startup', i.e., do both as applicable.
  --nobackup
        Do not make an automatic backup of the configuration file.
  -i, --input=FILE
        Select a FILE to input as the configuration file. Set FILE to '-' to
        pipe from standard input.  Without this option, aticonfig will search
        /etc/X11 for the default configuration file.
  -o, --output=FILE
        Select a FILE to output the new configuration file to.  Set FILE to '-'
        to print to standard output.  Without this option, aticonfig will
        replace the input file with the newly generated file.
  -h, --help
        Display this help screen.
  -f, --force
        Only valid with 'initial' option.  Force aticonfig to generate default
        Monitor, Device, and Screen sections even if the original configuration
        file has invalid settings in these sections.

Examples:
  1. Setting up fglrx for the first time.
       Single head :    aticonfig --initial --input=/etc/X11/xorg.conf
       Dual head   :    aticonfig --initial=dual-head --screen-layout=above
                        This command will generate a dual head configuration
                        file with the second screen located above the first
                        screen.
  2. Setting up big desktop to horizontal and set overlay on secondary display.
                        aticonfig --dtop=horizontal --overlay-on=1
  3. Setting up modes for primary display.
                        aticonfig --resolution=0,1600x1200,1280x1024,1024x768
  4. Force primary CRT on and TV-out off.
                        aticonfig --force-monitor=crt1,notv
  5. Change tv geometry 
                         aticonfig --tv-geometry=85x90+10-10 
         This will set tv to 85% width (where 100% ==
         overscan) 90% height and shift 10 pixels right of centre
         and 10 pixels down of centre. 

Please report bugs to [http://support.ati.com](http://support.ati.com)

What I'd like to do is do those --<whatever> commands, but it never lets me. I need some advice on how to get it goin' - I'm on 64-bit Ubuntu 8.04 Hardy with an amd64 CPU.

Also after running glxinfo | grep direct, I receive this:

direct rendering: No (If you want to find out why, try setting LIBGL_DEBUG=verbose)
OpenGL renderer string: Mesa GLX Indirect

Any way to turn on direct rendering? Been trying to research and have tried various methods, none have gotten ideal results.

Thanks.

---

### Post by spiderbatdad on 2008-05-21
Try: ```

aticonfig --initial --input=/etc/X11/xorg.conf
```

---

### Post by alexforcefive on 2008-05-21
That's not really an error message, it means that your xorg.conf is already set up. If you want to double check this, type "sudo gedit /etc/X11/xorg.conf". You should see something that looks like:

```
Section "Device"
	Identifier	"aticonfig-Device[0]"
	Driver		"fglrx"
	Option		"VideoOverlay" "true"
	Option		"OpenGLOverlay" "false"
EndSection
```

If you do, just restart your X server (restart your computer or hit ctrl+alt+backspace) and you should be good to go. If the "driver" part doesn't say "fglrx", change it before you restart.

---

### Post by =Fus3= on 2008-05-21
> **spiderbatdad said:**
> Try: ```

aticonfig --initial --input=/etc/X11/xorg.conf
```

Still the same. ):

Found fglrx primary device section
Nothing to do, terminating.

> That's not really an error message, it means that your xorg.conf is already set up. If you want to double check this, type "sudo gedit /etc/X11/xorg.conf". You should see something that looks like:

Code:

Section "Device"
	Identifier	"aticonfig-Device[0]"
	Driver		"fglrx"
	Option		"VideoOverlay" "true"
	Option		"OpenGLOverlay" "false"
EndSection

If you do, just restart your X server (restart your computer or hit ctrl+alt+backspace) and you should be good to go. If the "driver" part doesn't say "fglrx", change it before you restart.

This is what mine says, which is pretty similar to yours.

Section "Device"
	Identifier	"aticonfig-Device[0]"
	Driver		"fglrx"
	Option		"VideoOverlay"	"on"
	Option		"OpenGLOverlay"	"off"
EndSection

I've also tried restarting my computer, but it doesn't appear to affect anything. I still get said 'found nothing/terminating' message, and the direct rendering is off.

---

### Post by SunnyRabbiera on 2008-05-21
ATI cards are the bane of linux's existence, so dont be surprised when this doesn't work.

---

### Post by jocko on 2008-05-23
> **=Fus3= said:**
> Still the same. ):

Found fglrx primary device section
Nothing to do, terminating.



This is what mine says, which is pretty similar to yours.

Section "Device"
    Identifier    "aticonfig-Device[0]"
    Driver        "fglrx"
    Option        "VideoOverlay"    "on"
    Option        "OpenGLOverlay"    "off"
EndSection

I've also tried restarting my computer, but it doesn't appear to affect anything. I still get said 'found nothing/terminating' message, and the direct rendering is off.

The "found nothing/terminating" message simply means **"xorg.conf is already set up correctly and nothing needs to be done**".
If glxinfo reports that direct rendering is off, either you have xgl installed, which usually means glxinfo and fglrxinfo will not work properly and can't see that direct rendering is really working, or you have failed to install the driver.
Is the correct driver used?
What do you get from this:
```
cat /var/log/Xorg.0.log | grep EE
cat /var/log/Xorg.0.log | grep render
```
Which method did you use to install ther driver?

---

