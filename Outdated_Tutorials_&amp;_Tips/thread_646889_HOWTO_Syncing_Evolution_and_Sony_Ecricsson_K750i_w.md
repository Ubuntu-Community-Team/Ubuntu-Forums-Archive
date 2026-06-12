---
title: "HOWTO: Syncing Evolution and Sony Ecricsson K750i with Bluetooth."
date: 2007-12-21
forum: Outdated Tutorials &amp; Tips
---

### Post by masala on 2007-12-21
This is a HOWTO for synchronizing contacts, calendar and tasks between a Sony Ericsson K750i and Evolution via Bluetooth and the OpenSync framework (in theory it should not only work with the K750i but with any other device that provides the Bluetooth service *OBEX IrMC Sync Server*).

It has been tested with
[LIST]
[*]Ubuntu Gutsy (7.10)
[*]Evolution 2.12.1
[*]OpenSync 0.22
[/LIST]

This documentation is based on the following OpenSync documentation:
[LIST]
[*][http://www.opensync.org/wiki/SetupGuide]("http://www.opensync.org/wiki/SetupGuide")
[*][http://www.opensync.org/wiki/Evo2-File]("http://www.opensync.org/wiki/Evo2-File")
[/LIST]

[SIZE="4"]**1 - Install OpenSync**[/SIZE]

You need to add a new APT repository to get the OpenSync packages. Append the following line to the file [FONT="Courier New"]/etc/apt/sources.list[/FONT]

```
deb http://opensync.gforge.punktart.de/repo/opensync-0.21/ feisty main
```

(At the moment of writing, there was no section for Gutsy, but the Feisty repo works on Gutsy too)

Register the repository's key:

```

$ gpg --keyserver hkp://subkeys.pgp.net/ --recv-keys CB210090B029CB84
$ gpg --export CB210090B029CB84 | sudo apt-key add -

```

Now install the required packages:

```

$ sudo aptitude install libopensync-plugin-evolution2 libopensync-plugin-irmc multisync-gui opensyncutils msynctool

```

[SIZE="4"]**2 - Setup OpenSync**[/SIZE]

Create a new configuration:

```

$ msynctool --addgroup evolution-k750i

```

[SIZE="2"]**2.1 - Configure the Evolution side**[/SIZE]

```

$ msynctool --addmember evolution-k750i evo2-sync
$ msynctool --configure evolution-k750i 1

```

The second command opens an editor (probably *vi*). Edit the content as below:

```

<?xml version="1.0"?>
<config>
  <address_path>default</address_path>
  <calendar_path>default</calendar_path>
  <tasks_path>default</tasks_path>
</config>

```

You have just configured to use Evolution's *default* addressbook, calendar and task list for synchronization. See section 4 for how to use other than *default*.

[SIZE="2"]**2.2 - Configure the K750i side**[/SIZE]

```

$ msynctool --addmember evolution-k750i irmc-sync
$ msynctool --configure evolution-k750i 2

```

Again, the second command opens an editor. Edit the content as below:

```

<config>
  <connectmedium>bluetooth</connectmedium>
  <btunit>00:11:22:33:44:55</btunit>
  <btchannel>8</btchannel>
</config>

```

Replace [FONT="Courier New"]00:11:22:33:44:55[/FONT] with your phone's Bluetooth address. The channel should be ok for the K750i. However, you can get the channel number by running

```

$ sdptool browse 00:11:22:33:44:55

```

and searching the output for the service called * OBEX IrMC Sync Server*.

[SIZE="4"]**3 - Synchronize**[/SIZE]

You can now synchronize all data with the command below, ** but please read further before doing your first synchronization!**

```

$ msynctool --sync evolution-k750i --filter-objtype note

```

The parameter [FONT="Courier New"]--filter-objtype note[/FONT] avoids a bug. Synchronizing notes is currently not possible :(.

**:-$ Since OpenSync is still in its early development stage, it does not always work as expected. Hence, I recommend you synchronize only one data type at a time. You can do this by using the option [FONT="Courier New"]--filter-objtype[/FONT]!**

Only sync contacts:

```

$ msynctool --sync evolution-k750i --filter-objtype note  --filter-objtype event  --filter-objtype todo

```

Only sync calendar:

```

$ msynctool --sync evolution-k750i --filter-objtype note  --filter-objtype contact  --filter-objtype todo

```

Only sync tasks:

```

$ msynctool --sync evolution-k750i --filter-objtype note  --filter-objtype contact  --filter-objtype event

```

**In any case .. it is a very very good idea to backup your data in evolution and on the phone prior the first synchronizations.**

[SIZE="4"]**4 - Tips and tricks**[/SIZE]

[LIST]
[*]:!: If you want to sync other contacts, events or tasks than *default*, use the graphical tool *multisync-gui* to easily select another addressbook, calendar or task list. Acutally you can configure anything described above also with this tool. However, the filter configuration of *multisync-gui* has no effect yet (at least for me).
[*]In the future it is probably better to use the OpenSync *syncml* plugin instead of *irmc*. But at the moment the *syncml* plugin only works for contacts (at least with the K750i). Have a look at [http://www.opensync.org/wiki/syncml-guide]("http://www.opensync.org/wiki/syncml-guide") for updated information.

[*]When you have a lot of sync conflicts, you can automatically give precedence to either Evolution or the K750i. Just add the option [FONT="Courier New"]--conflict X[/FONT] when synchronizing. Replace X with 1 to prefer Evoltuion or 2 to prefer data from the K750i.

[*]:-k In my case contact synchronization did not work for contacts I created in Evolution by adding an e-mail attached VCARD to my addressbook.

[/LIST]

Feel free to ask any questions if something is not clear or does not work for you..

---

### Post by kabanta on 2008-01-01
This was a very helpful post! thanks.

Some quick comments:

[LIST]
[*]For "install the required packages", the list should include **msynctools** 
[*] **multisync-gui** seems buggy -- and you use the CLI for this entire howto -- so you may want to leave that off the list of packages to install
[/LIST]

my phone is w300i. i tried syncing only calendar items and it mostly worked, but some things worth noting in your howto:

[LIST]
[*]although it was possible to sync calendar events by following your CLI instructions, it was not possible using the equivalent multisync-gui interface
[*]repeated events do not seem to work (they either do not appear or are treated oddly)
[*]it is not obvious how to modify these instructions to have the sync work between the phone and a specific .ics file. when i edit the appropriate .gconf file and replace "default" with an actual path, it generates an error. (worse: if i try using the path with the multisync-gui interface, the file will be modified to delete the path information entirely.) altho i installed the opensync-file plugin, my guess is that the existence of the opensync-evolution plugin is somehow over-riding it and expecting "default."
[/LIST]

---

### Post by feenstra on 2008-02-14
I can select the set of calendars that I have in Evolution simply by name from the GUI. (Although I must say, I have not yet actually synced anything yet -- waiting for a moment when I feel braver than I do now ;-)

---

### Post by masala on 2008-02-18
> **kabanta said:**
> 
[LIST]
[*]For "install the required packages", the list should include **msynctools**
[/LIST]

You're right, just added the package.
> 
[LIST]
[*] **multisync-gui** seems buggy -- and you use the CLI for this entire howto -- so you may want to leave that off the list of packages to install
[/LIST]

The GUI is the more convinient way to sync to a non-default evolution addressbook, calender or tasklist. I just use the GUI for this task - it sets the approriate path values in step 2.1.

> 
[LIST]
[*]although it was possible to sync calendar events by following your CLI instructions, it was not possible using the equivalent multisync-gui interface
[/LIST]

Never tried this. I just use the GUI to set the address (etc.) path I would otherwise specify manually in step 2.1.
> 
[LIST]
[*]repeated events do not seem to work (they either do not appear or are treated oddly)
[/LIST]

Multisync (predecessor of OpneSync) had an option to convert repeated events to simple events if the target device does not support repeated events. OpenSync 0.22 still seems to miss this feature.
> 
[LIST]
[*]it is not obvious how to modify these instructions to have the sync work between the phone and a specific .ics file. when i edit the appropriate .gconf file and replace "default" with an actual path, it generates an error. (worse: if i try using the path with the multisync-gui interface, the file will be modified to delete the path information entirely.) altho i installed the opensync-file plugin, my guess is that the existence of the opensync-evolution plugin is somehow over-riding it and expecting "default."
[/LIST]
The same happens for me too, but it worked for me at least once, just cannot find the reason why it is not working anymore. Anyway, you can set a specific .ics file manually in step 2.1, for instance;

```

<?xml version="1.0"?>
<config>
  <address_path>default</address_path>
  <calendar_path>default</calendar_path>
  <tasks_path>file:///home/masala/.evolution/calendar/local/1198183015.6861.0@myhost</tasks_path>
</config>

```

Just adjust the path to your environment.

---

