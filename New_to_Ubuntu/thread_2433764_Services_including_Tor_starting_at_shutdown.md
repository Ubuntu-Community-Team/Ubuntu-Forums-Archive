---
title: "Services including Tor starting at shutdown"
date: 2019-12-25
forum: New to Ubuntu
---

### Post by oldman439 on 2019-12-25
Hello,

Lately when I shutdown my computer it takes a long time to power down, and on at least two occasions it has actually stayed on after the screen goes black (LEDs and fans still operating). So I started hitting Ctrl-Alt-F1 immediately after clicking Power Off, and this is what I see:

                        [FONT=Inconsolata]/dev/nvme2n1p2: clean, [/FONT][COLOR=#ce181e][FONT=Inconsolata]X/Y[/FONT][/COLOR][FONT=Inconsolata] files, [/FONT][COLOR=#ce181e][FONT=Inconsolata]X/Y[/FONT][/COLOR][FONT=Inconsolata] blocks.[/FONT]
 [FONT=Inconsolata][ [/FONT][COLOR=#2cee0e][FONT=Inconsolata]OK[/FONT][/COLOR][FONT=Inconsolata] ] Created slice User Slice of gdm.[/FONT]
 [FONT=Inconsolata]           Starting User Manager for UID 121&#8230;[/FONT]
[FONT=Inconsolata][ [/FONT][COLOR=#2cee0e][FONT=Inconsolata]OK[/FONT][/COLOR][FONT=Inconsolata] ] Started Session c1 of user gdm.[/FONT]
[FONT=Inconsolata][ [COLOR=#2cee0e]OK[/COLOR] ] Started User Manager for UID 121.[/FONT]
          [FONT=Inconsolata]Starting Daemon for power management&#8230;[/FONT]
[FONT=Inconsolata][ [COLOR=#2cee0e]OK[/COLOR] ] Started Daemon for power management.[/FONT]
 [FONT=Inconsolata][ [COLOR=#2cee0e]OK[/COLOR] ] Started Snappy daemon.[/FONT]
                       [FONT=Inconsolata]Starting Wait until snapd is fully seeded&#8230;[/FONT]
 [FONT=Inconsolata][ [COLOR=#2cee0e]OK[/COLOR] ] Started Wait until snapd is fully seeded.[/FONT]
          [FONT=Inconsolata]Starting RealtimeKit Scheduling Policy Service&#8230;[/FONT]
[FONT=Inconsolata][ [COLOR=#2cee0e]OK[/COLOR] ] Started RealtimeKit Scheduling Policy Service.[/FONT]
                             [FONT=Inconsolata]Starting Locale Service&#8230;[/FONT]
[FONT=Inconsolata][ [COLOR=#2cee0e]OK[/COLOR] ] Started Anonymizing overlay network for TCP.[/FONT]
 [FONT=Inconsolata][ [COLOR=#2cee0e]OK[/COLOR] ] Started Locale Service.[/FONT]
                            [FONT=Inconsolata]Starting Location Lookup Service&#8230;[/FONT]
         [FONT=Inconsolata]Starting Thunderbolt system service&#8230;[/FONT]
 [FONT=Inconsolata][ [COLOR=#2cee0e]OK[/COLOR] ] Started Location Lookup Service.[/FONT]
                            [FONT=Inconsolata]Starting PackageKit Daemon&#8230;[/FONT]
 [FONT=Inconsolata][ [COLOR=#2cee0e]OK[/COLOR] ] Started PackageKit Daemon.[/FONT]
 [FONT=Inconsolata][ [COLOR=#2cee0e]OK[/COLOR] ] Started Thunderbolt system service.

This disk partition isn't visible using GParted, and I think one of the services is Tor. Is this normal to see at shutdown? I don't want to jump to conclusions or get paranoid about things that I admittedly don't fully grasp yet.Any knowledge is appreciated.
[/FONT]

---

