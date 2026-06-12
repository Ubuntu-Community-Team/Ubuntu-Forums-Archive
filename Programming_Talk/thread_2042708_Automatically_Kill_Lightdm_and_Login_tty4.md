---
title: "Automatically Kill Lightdm and Login tty4"
date: 2012-08-15
forum: Programming Talk
---

### Post by Dr.Paneas on 2012-08-15
I want to write script that does the following:

kill the X server and stop lightdm
[PHP]
kill_X()
{
  # Stop the xserver (lightdm)
  sudo chvt 4 && sudo service lightdm stop
}
[/PHP]

Then I want to login automatically to tty4 and automatically run the script itself.
[PHP]
auto_run_script()
{
 if [ -s ~/.bash_profile ]; then
    cp ~/.bash_profile ~/.bash_profile.backup    
    test=`grep "sh $PWD/$0" ~/.bash_profile`
    if [ -z "$test" ]; then
        echo "sh $PWD/$0" >> ~/.bash_profile
    fi
 else
    echo "sh $PWD/$0" >> ~/.bash_profile
 fi
}
[/PHP]

and for the autologin part I use the Upstart
[php]
    goto=/etc/init

    # backup
    sudo cp $goto/tty1.conf $goto/tty1.conf.backup
    b=--autologin
    
    sudo sed -i 's_/sbin/getty_/sbin/mingetty_g' /etc/init/tty1.conf

    b3=`awk '/exec/ { print $3 } ' /etc/init/tty1.conf`
    sudo sed -i "s/$b3/$b/g" /etc/init/tty1.conf

    b4=`awk '/exec/ { print $4 } ' /etc/init/tty1.conf`
    sudo sed -i "s/$b4/$us3r/g" /etc/init/tty1.conf
[/php]

The problem is that when I kill X server, the automated login doesn't work. I have to reboot the computer in order to "confirm" the change in Upstart. Is there any way to do it without restarting ?

---

