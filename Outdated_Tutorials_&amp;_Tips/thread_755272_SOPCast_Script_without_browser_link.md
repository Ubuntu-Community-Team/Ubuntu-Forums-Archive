---
title: "SOPCast Script without browser link"
date: 2008-04-14
forum: Outdated Tutorials &amp; Tips
---

### Post by fieldyweb on 2008-04-14
I was trying to find a way to run Sopcast using the sop:// address without the need of a browser, not sure if anyone will find this useful, however its a small script i put together, to use the command line and VLC to view Sopcast broadcasts.

There is an alternative guid to set this up at:

> [http://www.linux.ryukent.co.uk/show.php?id=36]("http://www.linux.ryukent.co.uk/show.php?id=36")

I'm not however using the Firefox brosser link, so setup as above, until you reach the Firefox broser about:config section, then you can use the following script, which will ask you for the sop:// address, then ask you if you are happy launching the VLC browser, you can tweak this to your hearts content.

[INDENT]> #!/bin/sh

ZEN="/usr/bin/zenity --title SopCast"

# 20 second countdown in fives
function countdown() {
    for i in $(seq 0 5 100)
    do
        echo ${i}
        sleep 1
    done
}


szSOPCAST=$(zenity --entry --text "Enter the SopCast URL here" --entry-text "sop
://...")
sp-sc $szSOPCAST  3908 8908 &

countdown()
${ZEN} --question --text="Launch VLC"

# if clicked 'OK' run VLC, else exit
if [[ "${?}" -eq "0" ]]
then
	vlc [http://localhost:8908/tv.asf](http://localhost:8908/tv.asf)
	killall -9 sp-sc
else
    killall -9 sp-sc
    exit 1
fi
[/INDENT]

What should happen is the sopcast stream becomes visable in your terminal, then after 20 seconds, you are prompted to run VLC

Remove the line countdown() if you want the prompt to appear immediately..

Additional functionality, and constructive comments welcome as always

---

### Post by flyguy97 on 2009-01-06
I have also written a front-end for SopCast. It integrates VLC on the UI so no need to open a separate program. You can also open many instances of the player and watch different channels if you like, the port assignments for viewing are dynamic so different instances won't "step on each other". Let me know what you think.

[http://code.google.com/p/sopcast-player]("http://code.google.com/p/sopcast-player")

btw. Be sure to read the Installation notes on the website before you install, due to the GPL I am unable to include the SopCast client program in the package.

flyguy97

---

