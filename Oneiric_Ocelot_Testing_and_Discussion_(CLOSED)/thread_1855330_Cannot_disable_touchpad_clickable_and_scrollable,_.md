---
title: "Cannot disable touchpad clickable and scrollable,  Adjust screen brightness failed."
date: 2011-10-06
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by shoutrain on 2011-10-06
My PC: Lenovo K47G, i7 2630QM (Core Graph)

Everything is ok with Windows 7 64-bit.  There are some issues with Linux.

After I installed newest Ubuntu (11.10 beta 2):

[LIST=1]
[*]Cannot disable touchpad clickable and enable scrollable,  although there is Touchpad settings,
[*]Adjust screen brightness failed, although the brightness progress bar can show up, makes no sense.  I am sure I have Intel® Sandybridge Mobile x86 driver installed because I can find the information in the setting and lspic(below).
[/LIST]


Additional, I meet the same situation except there is no Touchpad setting with Fedora 15.

[COLOR=Blue]rafael@rafael-k47g:~$ lspci
00:00.0 Host bridge: Intel Corporation 2nd Generation Core Processor Family DRAM Controller (rev 09)
00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09)
00:16.0 Communication controller: Intel Corporation 6 Series/C200 Series Chipset Family MEI Controller #1 (rev 04)
00:19.0 Ethernet controller: Intel Corporation 82579V Gigabit Network Connection (rev 05)
00:1a.0 USB Controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #2 (rev 05)
00:1b.0 Audio device: Intel Corporation 6 Series/C200 Series Chipset Family High Definition Audio Controller (rev 05)
00:1c.0 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 1 (rev b5)
00:1c.2 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 3 (rev b5)
00:1d.0 USB Controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #1 (rev 05)
00:1f.0 ISA bridge: Intel Corporation HM65 Express Chipset Family LPC Controller (rev 05)
00:1f.2 SATA controller: Intel Corporation 6 Series/C200 Series Chipset Family 6 port SATA AHCI Controller (rev 05)
00:1f.3 SMBus: Intel Corporation 6 Series/C200 Series Chipset Family SMBus Controller (rev 05)
05:00.0 Network controller: Intel Corporation Centrino Wireless-N 1000[/COLOR]

---

### Post by sammiev on 2011-10-06
Have you tried this yet?

---

### Post by sonicb00m on 2011-10-06
If you type

xinput list

Do you have an ALP touchpad? If so that will be the reason. The driver is not supported by X and the touchpad settings don't work. I have this very problem with my Vostro

I wrote a script to turn mine off when the USB mouse is plugged in

```


ID=$(xinput list | grep 'ALPS' |  awk '{print $6}' | sed 's/id=//g')

                if xinput list | grep 'USB Mouse' > /dev/null ; then
                        xinput set-prop "$ID" "Device Enabled" 0
                else
                        xinput set-prop "$ID" "Device Enabled" 1

                        #check for idle time
                        IDLE=$(xprintidle)

                        if [[ $IDLE -lt 500 ]]; then
                                echo "xtouch disabled $IDLE"
        #                       xinput set-prop "$ID" "Device Enabled" 0
                        else
                                echo "xtouch enabled  $IDLE"
        #                       xinput set-prop "$ID" "Device Enabled" 1
                        fi

                fi

```

You'll need to add a loop and run it at startup.

p.s. I tried adding Idle time but to disable the mouse while typing but it doesn't work since moving the mouse resets the idle time.

---

### Post by shoutrain on 2011-10-06
> **sammiev said:**
> Have you tried this yet?

Yes, I tried.  But it doesn't work.

---

### Post by shoutrain on 2011-10-06
> **sonicb00m said:**
> If you type

xinput list

Do you have an ALP touchpad? If so that will be the reason. The driver is not supported by X and the touchpad settings don't work. I have this very problem with my Vostro

I wrote a script to turn mine off when the USB mouse is plugged in

```


ID=$(xinput list | grep 'ALPS' |  awk '{print $6}' | sed 's/id=//g')

                if xinput list | grep 'USB Mouse' > /dev/null ; then
                        xinput set-prop "$ID" "Device Enabled" 0
                else
                        xinput set-prop "$ID" "Device Enabled" 1

                        #check for idle time
                        IDLE=$(xprintidle)

                        if [[ $IDLE -lt 500 ]]; then
                                echo "xtouch disabled $IDLE"
        #                       xinput set-prop "$ID" "Device Enabled" 0
                        else
                                echo "xtouch enabled  $IDLE"
        #                       xinput set-prop "$ID" "Device Enabled" 1
                        fi

                fi

```You'll need to add a loop and run it at startup.

p.s. I tried adding Idle time but to disable the mouse while typing but it doesn't work since moving the mouse resets the idle time.


Right, sonicb00m, it's ALP touchpad.  I will try your script in a loop as a service.  Thank you very much:)

---

### Post by shoutrain on 2011-10-11
> **shoutrain said:**
> Right, sonicb00m, it's ALP touchpad.  I will try your script in a loop as a service.  Thank you very much:)

I tried, looks this script doesn't work in my laptop.  

And I tried the commands from the script you gave me manually:
rafael@rafael-K47G:~$ sudo xinput list | grep 'ALPS' | awk '{print $6}' | sed 's/id=//g'
13
rafael@rafael-K47G:~$ sudo xinput set-prop "13" "Device Enabled" 0

But it cannot disable the touchpad.

---

### Post by shoutrain on 2011-10-11
> **sonicb00m said:**
> If you type

xinput list

Do you have an ALP touchpad? If so that will be the reason. The driver is not supported by X and the touchpad settings don't work. I have this very problem with my Vostro

I wrote a script to turn mine off when the USB mouse is plugged in

```


ID=$(xinput list | grep 'ALPS' |  awk '{print $6}' | sed 's/id=//g')

                if xinput list | grep 'USB Mouse' > /dev/null ; then
                        xinput set-prop "$ID" "Device Enabled" 0
                else
                        xinput set-prop "$ID" "Device Enabled" 1

                        #check for idle time
                        IDLE=$(xprintidle)

                        if [[ $IDLE -lt 500 ]]; then
                                echo "xtouch disabled $IDLE"
        #                       xinput set-prop "$ID" "Device Enabled" 0
                        else
                                echo "xtouch enabled  $IDLE"
        #                       xinput set-prop "$ID" "Device Enabled" 1
                        fi

                fi

```You'll need to add a loop and run it at startup.

p.s. I tried adding Idle time but to disable the mouse while typing but it doesn't work since moving the mouse resets the idle time.


Actually, when I disable PS/2 Mouse instead of AlpsPS/2 ALPS GlidePoint, it works:P.

Looks AlpsPS/2 ALPS GlidePoint doesn't work in my laptop at all.

Thank you

---

### Post by sonicb00m on 2011-10-11
Glad you found a solution in the end! Hopefully there will be proper support for this in the future.

---

