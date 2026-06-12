---
title: "Python bash application"
date: 2018-04-10
forum: Programming Talk
---

### Post by ikitissimo on 2018-04-10
Hi everyone, i'm a self teaching absolute beginner young developer and i'm playing with some coding to make a simple application to create backups of folders/files.

First i created this simple Backup.sh in Ubuntu server 16.04:
```

#!/bin/bash

LOGFILE=/home/user/Desktop/Backup_log.log

SRCDIR="/home/user/Desktop/folder_to_backup/"

DESTDIR="/home/user/Desktop/destination_folder_for_backup/"

echo "$(date +%-Y-%m-%d-+%-T) : Beginning Backup" >> $LOGFILE 2>&1
echo "$(date +%-Y-%m-%d-+%-T) : Preparing '$SRCDIR'" >> $LOGFILE 2>&1

FILENAME=Archive-$(date +%-Y-%m-%d)-$/date +%-T).tgz

tar --create --gzip --file=$DESTDIR$FILENAME $SRCDIR >> LOGFILE 2>&1

echo "$(date +%-Y-%m-%d-+%-T) : Created $FILENAME'" >> $LOGFILE 2>&1
echo "$(date +%-Y-%m-%d-+%-T) : Destination '$DESTDIR'" >> $LOGFILE 2>&1

echo "$(date +%-Y-%m-%d-+%-T) :Verify content '$DESTDIR'" >> $LOGFILE 2>&1

ls -x -h --size --color $DESTDIR >> LOGFILE 2>&1

# tail /home/user/Desktop/Backup_log.log

exit

```

------------------------------------------------------------------------------------------------

Then with Glade 3.18 i tried to create a simple GUI in python:
```

<?xml version="1.0" encoding="UTF-8"?>
<!-- Generated with glade 3.18.3 -->
<interface>
  <requires lib="gtk+" version="3.12"/>
  <object class="GtkDialog" id="dialog1">
    <property name="can_focus">False</property>
    <property name="modal">True</property>
    <property name="default_width">800</property>
    <property name="default_height">480</property>
    <property name="type_hint">dialog</property>
    <child internal-child="vbox">
      <object class="GtkBox" id="dialog-vbox1">
        <property name="can_focus">False</property>
        <property name="orientation">vertical</property>
        <property name="spacing">2</property>
        <child internal-child="action_area">
          <object class="GtkButtonBox" id="dialog-action_area1">
            <property name="can_focus">False</property>
            <property name="layout_style">end</property>
            <child>
              <object class="GtkButton" id="button1">
                <property name="label" translatable="yes">Continue</property>
                <property name="visible">True</property>
                <property name="can_focus">True</property>
                <property name="receives_default">True</property>
              </object>
              <packing>
                <property name="expand">True</property>
                <property name="fill">True</property>
                <property name="position">0</property>
              </packing>
            </child>
            <child>
              <object class="GtkButton" id="button2">
                <property name="label" translatable="yes">Exit</property>
                <property name="visible">True</property>
                <property name="can_focus">True</property>
                <property name="receives_default">True</property>
              </object>
              <packing>
                <property name="expand">True</property>
                <property name="fill">True</property>
                <property name="position">1</property>
              </packing>
            </child>
          </object>
          <packing>
            <property name="expand">False</property>
            <property name="fill">False</property>
            <property name="position">1</property>
          </packing>
        </child>
        <child>
          <object class="GtkLabel" id="What to Backup">
            <property name="visible">True</property>
            <property name="can_focus">False</property>
            <property name="label" translatable="yes">What to Backup</property>
          </object>
          <packing>
            <property name="expand">False</property>
            <property name="fill">True</property>
            <property name="position">0</property>
          </packing>
        </child>
        <child>
          <object class="GtkFileChooserButton" id="filechooserbutton2">
            <property name="visible">True</property>
            <property name="can_focus">False</property>
          </object>
          <packing>
            <property name="expand">False</property>
            <property name="fill">True</property>
            <property name="position">1</property>
          </packing>
        </child>
        <child>
          <object class="GtkLabel" id="Destination">
            <property name="visible">True</property>
            <property name="can_focus">False</property>
            <property name="label" translatable="yes">Destination</property>
          </object>
          <packing>
            <property name="expand">False</property>
            <property name="fill">True</property>
            <property name="position">2</property>
          </packing>
        </child>
        <child>
          <object class="GtkFileChooserButton" id="filechooserbutton1">
            <property name="visible">True</property>
            <property name="can_focus">False</property>
          </object>
          <packing>
            <property name="expand">False</property>
            <property name="fill">True</property>
            <property name="position">4</property>
          </packing>
        </child>
      </object>
    </child>
  </object>
</interface>

```

What i would like to do now is:
-Use the folder selected with the "What to Backup" button as the variable $SRCDIR
-Use the directory chosen with the "Destination" button as the variable $DESTDIR
-Make the "Continue" button execute tar
-Make the "Exit" button close the application

I would leave the "ls" and "tail" commands behind for now since they only helped me to check if the script worked as intended.
Maybe these are stupid questions but any help on what to do or where to begin is really appreciated.
Thank you all

---

### Post by spjackson on 2018-04-13
Welcome to the forums.

Please show your python code. Do you want the "Continue" button to execute tar directly or to call your bash script?

---

### Post by logix2 on 2018-04-13
To create a GUI for Bash scripts, I would recommend YAD: [https://sourceforge.net/p/yad-dialog/wiki/Examples/](https://sourceforge.net/p/yad-dialog/wiki/Examples/)

---

