---
title: "HOWTO: Control XMMS remotely using your mobile phone"
date: 2006-02-18
forum: Outdated Tutorials &amp; Tips
---

### Post by cronholio on 2006-02-18
This is really sweet if you get it to work and it shouldn't be too hard. 

What you need:

-Ubuntu (I did it in Breezy, may work in other releases)
-XMMS installed
-A Bluetooth dongle or whatever kind of built-in Bluetooth support
-A Symbian powered mobile phone, like Nokia series 60 (7650/3650) or Siemens P800/P900

(If you have a different type of mobile phone, you may be have a look [here]("http://bemused.sourceforge.net/related/") and see if it is supported by some other software.)

Now, open a terminal and do this:

```
sudo apt-get install gnome-bluetooth
sudo apt-get install libgtk1.2-dev
sudo apt-get install xmms-dev
sudo apt-get install libbluetooth1-dev
```

Visit [this site]("http://bemused.sourceforge.net/downloads") and download the file for your type of phone, then extract the file bemused.sis from the archive. You can delete the archive file now because it contains the Windoze version of the server and we don't want that.

Now you need to send bemused.sis to your phone. Enable Bluetooth in your phone's settings. In the terminal, enter:

```
hcitool scan
```

After a while, the name of your phone should appear. Now switch to the directory that contains bemused.sis and enter:

```
gnome-obex-send bemused.sis
```

A dialog box will appear in Gnome. Select your phone and press okay. You should receive the file now and install it on the mobile phone.

(Optional: Install [this]("http://www.grumz.net/index.php?q=taxonomy/term/2/9") and include "gnome-obex-send" into your nautilus right-click menu for convenient future use if you want to.)

Now, download "Source code for the Bemused Linux server" from [here]("http://bemused.sourceforge.net/downloads") and extract it. In the terminal window, switch to the directory that you just extracted and do this:

```
sdptool add --channel=9 SP
sudo make install
```

If it doesn't work, post here. If it does, do:

```
sudo gedit /etc/bemused.conf
```

Change the line containing "channel" to:

```
channel=9
```

(Remove the leading "#")

Change the line containing mp3dir so it points to your mp3 directory. Change some more settings if you know what you're doing. Save and quit.

Make sure that XMMS is NOT running. In the terminal, type:

```
bemusedlinuxserver -d
```

XMMS should start. Run the Bemused software on your phone and enjoy.

If you want, you can go to Applications->System Tools->Applications Menu Editor and create a new entry for bemusedlinuxserver.

Have fun!

---

### Post by corona1 on 2006-03-15
Does anyone know if/how this can be done with a Motorola Razr or V360?

---

### Post by woifi on 2006-03-17
does this work with beep media player too?

edit: yes, it does work! unfortunately i can't read the playlist at my mobile, there are just cryptic symbols...

---

### Post by corona1 on 2006-03-17
[QUOTE=woifi]does this work with beep media player too?

edit: yes, it does work! unfortunately i can't read the playlist at my mobile, there are just cryptic symbols...[/QUOTE]

What model phone?

---

### Post by woifi on 2006-03-19
Siemens SX1

---

### Post by tobbworld on 2006-10-24
Hi,

I tried to install bemusedserver, but I get following error:
> 
 make install
g++ -o bemusedlinuxserver -I/usr/include/xmms -I./ -lxmms -lbluetooth `gtk-config --libs --cflags` main.cpp BemusedServerDlg.cpp
/bin/sh: gtk-config: command not found
BemusedServerDlg.cpp:41:33: Fehler: bluetooth/bluetooth.h: No such file or directory
BemusedServerDlg.cpp:42:30: Fehler: bluetooth/rfcomm.h: No such file or directory
BemusedServerDlg.cpp:49:22: Fehler: xmmsctrl.h: No such file or directory
BemusedServerDlg.cpp:154: Fehler: »bdaddr_t« bezeichnet keinen Typ
BemusedServerDlg.cpp: In member function »bool CBemusedServerDlg::CheckWinamp(const char*)«:
BemusedServerDlg.cpp:607: Fehler: »xmms_remote_is_running« wurde in diesem Gültigkeitsbereich nicht definiert
BemusedServerDlg.cpp:616: Fehler: »xmms_remote_is_running« wurde in diesem Gültigkeitsbereich nicht definiert
BemusedServerDlg.cpp: In member function »void CBemusedServerDlg::FadeOut()«:
BemusedServerDlg.cpp:624: Fehler: »xmms_remote_get_main_volume« wurde in diesem Gültigkeitsbereich nicht definiert
BemusedServerDlg.cpp:630: Fehler: »xmms_remote_set_main_volume« wurde in diesem Gültigkeitsbereich nicht definiert
BemusedServerDlg.cpp:633: Fehler: »xmms_remote_set_main_volume« wurde in diesem Gültigkeitsbereich nicht definiert
BemusedServerDlg.cpp: In member function »void CBemusedServerDlg::WriteDetailedInfoToPhone()«:
BemusedServerDlg.cpp:653: Fehler: »xmms_remote_get_info« wurde in diesem Gültigkeitsbereich nicht definiert
BemusedServerDlg.cpp: In member function »void CBemusedServerDlg::WriteInfoToPhone()«:
BemusedServerDlg.cpp:701: Fehler: »xmms_remote_get_playlist_pos« wurde in diesem Gültigkeitsbereich nicht definiert
BemusedServerDlg.cpp:701: Fehler: »xmms_remote_get_playlist_time« wurde in diesem Gültigkeitsbereich nicht definiert
BemusedServerDlg.cpp:710: Fehler: »xmms_remote_is_playing« wurde in diesem Gültigkeitsbereich nicht definiert
BemusedServerDlg.cpp:711: Fehler: »xmms_remote_is_paused« wurde in diesem Gültigkeitsbereich nicht definiert
BemusedServerDlg.cpp:714: Fehler: »xmms_remote_get_output_time« wurde in diesem Gültigkeitsbereich nicht definiert
BemusedServerDlg.cpp:722: Fehler: »xmms_remote_is_repeat« wurde in diesem Gültigkeitsbereich nicht definiert
BemusedServerDlg.cpp:723: Fehler: »xmms_remote_is_shuffle« wurde in diesem Gültigkeitsbereich nicht definiert
BemusedServerDlg.cpp:732: Fehler: »xmms_remote_get_playlist_pos« wurde in diesem Gültigkeitsbereich nicht definiert
BemusedServerDlg.cpp:732: Fehler: »xmms_remote_get_playlist_title« wurde in diesem Gültigkeitsbereich nicht definiert
BemusedServerDlg.cpp: In member function »void CBemusedServerDlg::WriteInf2ToPhone()«:
BemusedServerDlg.cpp:777: Fehler: »xmms_remote_get_playlist_pos« wurde in diesem Gültigkeitsbereich nicht definiert
BemusedServerDlg.cpp:777: Fehler: »xmms_remote_get_playlist_time« wurde in diesem Gültigkeitsbereich nicht definiert
BemusedServerDlg.cpp:786: Fehler: »xmms_remote_is_playing« wurde in diesem Gültigkeitsbereich nicht definiert
BemusedServerDlg.cpp:787: Fehler: »xmms_remote_is_paused« wurde in diesem Gültigkeitsbereich nicht definiert
BemusedServerDlg.cpp:790: Fehler: »xmms_remote_get_output_time« wurde in diesem Gültigkeitsbereich nicht definiert
BemusedServerDlg.cpp:798: Fehler: »xmms_remote_is_repeat« wurde in diesem Gültigkeitsbereich nicht definiert
BemusedServerDlg.cpp:799: Fehler: »xmms_remote_is_shuffle« wurde in diesem Gültigkeitsbereich nicht definiert
BemusedServerDlg.cpp:808: Fehler: »xmms_remote_get_playlist_pos« wurde in diesem Gültigkeitsbereich nicht definiert
BemusedServerDlg.cpp:808: Fehler: »xmms_remote_get_playlist_title« wurde in diesem Gültigkeitsbereich nicht definiert
BemusedServerDlg.cpp: In member function »void CBemusedServerDlg::SetSeek()«:
BemusedServerDlg.cpp:861: Fehler: »xmms_remote_jump_to_time« wurde in diesem Gültigkeitsbereich nicht definiert
BemusedServerDlg.cpp: In member function »void CBemusedServerDlg::GetVolume()«:
BemusedServerDlg.cpp:869: Fehler: »xmms_remote_get_main_volume« wurde in diesem Gültigkeitsbereich nicht definiert
BemusedServerDlg.cpp: In member function »void CBemusedServerDlg::RemoveAllFromPlaylist()«:
BemusedServerDlg.cpp:897: Fehler: »xmms_remote_stop« wurde in diesem Gültigkeitsbereich nicht definiert
BemusedServerDlg.cpp:898: Fehler: »xmms_remote_playlist_clear« wurde in diesem Gültigkeitsbereich nicht definiert
BemusedServerDlg.cpp: In member function »void CBemusedServerDlg::SelectInPlaylist()«:
BemusedServerDlg.cpp:915: Fehler: »xmms_remote_set_playlist_pos« wurde in diesem Gültigkeitsbereich nicht definiert
BemusedServerDlg.cpp: In member function »void CBemusedServerDlg::PlayFile(bool)«:
BemusedServerDlg.cpp:990: Fehler: »xmms_remote_playlist_clear« wurde in diesem Gültigkeitsbereich nicht definiert
BemusedServerDlg.cpp:994: Fehler: »GList« wurde in diesem Gültigkeitsbereich nicht definiert
BemusedServerDlg.cpp:994: Fehler: »list« wurde in diesem Gültigkeitsbereich nicht definiert
BemusedServerDlg.cpp:995: Fehler: »gchar« wurde in diesem Gültigkeitsbereich nicht definiert
BemusedServerDlg.cpp:995: Fehler: expected primary-expression before »)« token
BemusedServerDlg.cpp:995: Fehler: »g_strdup« wurde in diesem Gültigkeitsbereich nicht definiert
BemusedServerDlg.cpp:995: Fehler: »g_list_append« wurde in diesem Gültigkeitsbereich nicht definiert
BemusedServerDlg.cpp:996: Fehler: »xmms_remote_playlist_add« wurde in diesem Gültigkeitsbereich nicht definiert
BemusedServerDlg.cpp:997: Fehler: »g_list_free« wurde in diesem Gültigkeitsbereich nicht definiert
BemusedServerDlg.cpp:1002: Fehler: »xmms_remote_play« wurde in diesem Gültigkeitsbereich nicht definiert
BemusedServerDlg.cpp:1014: Fehler: »xmms_remote_get_playlist_pos« wurde in diesem Gültigkeitsbereich nicht definiert
BemusedServerDlg.cpp:1014: Fehler: »xmms_remote_get_playlist_time« wurde in diesem Gültigkeitsbereich nicht definiert
BemusedServerDlg.cpp: In member function »void CBemusedServerDlg::SetVolume()«:
BemusedServerDlg.cpp:1146: Fehler: »xmms_remote_set_main_volume« wurde in diesem Gültigkeitsbereich nicht definiert
BemusedServerDlg.cpp: In member function »void CBemusedServerDlg::Play()«:
BemusedServerDlg.cpp:1153: Fehler: »xmms_remote_get_playlist_length« wurde in diesem Gültigkeitsbereich nicht definiert
BemusedServerDlg.cpp:1155: Fehler: »xmms_remote_play« wurde in diesem Gültigkeitsbereich nicht definiert
BemusedServerDlg.cpp: In member function »void CBemusedServerDlg::Stop(bool)«:
BemusedServerDlg.cpp:1167: Fehler: »xmms_remote_stop« wurde in diesem Gültigkeitsbereich nicht definiert
BemusedServerDlg.cpp:1169: Fehler: »xmms_remote_stop« wurde in diesem Gültigkeitsbereich nicht definiert
BemusedServerDlg.cpp: In member function »void CBemusedServerDlg::Pause()«:
BemusedServerDlg.cpp:1176: Fehler: »xmms_remote_pause« wurde in diesem Gültigkeitsbereich nicht definiert
BemusedServerDlg.cpp: In member function »void CBemusedServerDlg::NextTrack()«:
BemusedServerDlg.cpp:1182: Fehler: »xmms_remote_playlist_next« wurde in diesem Gültigkeitsbereich nicht definiert
BemusedServerDlg.cpp:1189: Fehler: »xmms_remote_get_playlist_pos« wurde in diesem Gültigkeitsbereich nicht definiert
BemusedServerDlg.cpp:1189: Fehler: »xmms_remote_get_playlist_time« wurde in diesem Gültigkeitsbereich nicht definiert
BemusedServerDlg.cpp: In member function »void CBemusedServerDlg::PreviousTrack()«:
BemusedServerDlg.cpp:1198: Fehler: »xmms_remote_playlist_prev« wurde in diesem Gültigkeitsbereich nicht definiert
BemusedServerDlg.cpp:1205: Fehler: »xmms_remote_get_playlist_pos« wurde in diesem Gültigkeitsbereich nicht definiert
BemusedServerDlg.cpp:1205: Fehler: »xmms_remote_get_playlist_time« wurde in diesem Gültigkeitsbereich nicht definiert
BemusedServerDlg.cpp: In member function »void CBemusedServerDlg::FastForward()«:
BemusedServerDlg.cpp:1213: Fehler: »xmms_remote_get_output_time« wurde in diesem Gültigkeitsbereich nicht definiert
BemusedServerDlg.cpp:1214: Fehler: »xmms_remote_jump_to_time« wurde in diesem Gültigkeitsbereich nicht definiert
BemusedServerDlg.cpp: In member function »void CBemusedServerDlg::Rewind()«:
BemusedServerDlg.cpp:1228: Fehler: »xmms_remote_get_output_time« wurde in diesem Gültigkeitsbereich nicht definiert
BemusedServerDlg.cpp:1231: Fehler: »xmms_remote_jump_to_time« wurde in diesem Gültigkeitsbereich nicht definiert
BemusedServerDlg.cpp: In member function »void CBemusedServerDlg::Shuffle()«:
BemusedServerDlg.cpp:1248: Fehler: »xmms_remote_is_shuffle« wurde in diesem Gültigkeitsbereich nicht definiert
BemusedServerDlg.cpp:1248: Fehler: »xmms_remote_toggle_shuffle« wurde in diesem Gültigkeitsbereich nicht definiert
BemusedServerDlg.cpp:1251: Fehler: »xmms_remote_is_shuffle« wurde in diesem Gültigkeitsbereich nicht definiert
BemusedServerDlg.cpp:1251: Fehler: »xmms_remote_toggle_shuffle« wurde in diesem Gültigkeitsbereich nicht definiert
BemusedServerDlg.cpp: In member function »void CBemusedServerDlg::Repeat()«:
BemusedServerDlg.cpp:1270: Fehler: »xmms_remote_is_repeat« wurde in diesem Gültigkeitsbereich nicht definiert
BemusedServerDlg.cpp:1270: Fehler: »xmms_remote_toggle_repeat« wurde in diesem Gültigkeitsbereich nicht definiert
BemusedServerDlg.cpp:1273: Fehler: »xmms_remote_is_repeat« wurde in diesem Gültigkeitsbereich nicht definiert
BemusedServerDlg.cpp:1273: Fehler: »xmms_remote_toggle_repeat« wurde in diesem Gültigkeitsbereich nicht definiert
BemusedServerDlg.cpp: In member function »void CBemusedServerDlg::WritePlaylistToPhone()«:
BemusedServerDlg.cpp:1382: Fehler: »xmms_remote_get_playlist_pos« wurde in diesem Gültigkeitsbereich nicht definiert
BemusedServerDlg.cpp:1383: Fehler: »xmms_remote_get_playlist_length« wurde in diesem Gültigkeitsbereich nicht definiert
BemusedServerDlg.cpp:1402: Fehler: »xmms_remote_get_playlist_title« wurde in diesem Gültigkeitsbereich nicht definiert
BemusedServerDlg.cpp: In member function »int CBemusedServerDlg::BluetoothConnectToSocket(int)«:
BemusedServerDlg.cpp:1794: Fehler: Aggregat »sockaddr_rc loc_addr« hat unvollständigen Typ und kann nicht definiert werden
BemusedServerDlg.cpp:1821: Fehler: »BTPROTO_RFCOMM« wurde in diesem Gültigkeitsbereich nicht definiert
BemusedServerDlg.cpp:1835: Fehler: »bdaddr« wurde in diesem Gültigkeitsbereich nicht definiert
BemusedServerDlg.cpp: In member function »int CBemusedServerDlg::BluetoothWaitforConnect(int)«:
BemusedServerDlg.cpp:1889: Fehler: »bdaddr_t« wurde in diesem Gültigkeitsbereich nicht definiert
BemusedServerDlg.cpp:1889: Fehler: expected `;' before »ba«
BemusedServerDlg.cpp:1890: Fehler: Aggregat »sockaddr_rc rem_addr« hat unvollständigen Typ und kann nicht definiert werden
BemusedServerDlg.cpp:1919: Fehler: »ba« wurde in diesem Gültigkeitsbereich nicht definiert
BemusedServerDlg.cpp:1919: Fehler: »baswap« wurde in diesem Gültigkeitsbereich nicht definiert
BemusedServerDlg.cpp:1923: Fehler: »batostr« wurde in diesem Gültigkeitsbereich nicht definiert
BemusedServerDlg.cpp: In member function »void CBemusedServerDlg::Log(char*, ...)«:
BemusedServerDlg.cpp:1939: Fehler: »va_start« wurde in diesem Gültigkeitsbereich nicht definiert
BemusedServerDlg.cpp:1941: Fehler: »va_end« wurde in diesem Gültigkeitsbereich nicht definiert
make: *** [bemusedlinuxserver] Fehler 1


Can you help, please?

Thanks a lot.

Tobbe

---

### Post by tobbworld on 2006-10-24
I forget.. I´m using Kubuntu Drapper Drake ;)

---

### Post by rado_london on 2006-10-24
```
rado@ubuntu:~/bemusedlinuxserver1.73$ sudo make install
g++ -o bemusedlinuxserver -I/usr/include/xmms -I./ -lxmms -lbluetooth `gtk-config --libs --cflags` main.cpp BemusedServerDlg.cpp
BemusedServerDlg.cpp:41:33: error: bluetooth/bluetooth.h: No such file or directory
BemusedServerDlg.cpp:42:30: error: bluetooth/rfcomm.h: No such file or directoryBemusedServerDlg.cpp:154: error: ‘bdaddr_t’ does not name a type
BemusedServerDlg.cpp: In member function ‘int CBemusedServerDlg::BluetoothConnectToSocket(int)’:
BemusedServerDlg.cpp:1794: error: aggregate ‘sockaddr_rc loc_addr’ has incomplete type and cannot be defined
BemusedServerDlg.cpp:1821: error: ‘BTPROTO_RFCOMM’ was not declared in this scope
BemusedServerDlg.cpp:1835: error: ‘bdaddr’ was not declared in this scope
BemusedServerDlg.cpp: In member function ‘int CBemusedServerDlg::BluetoothWaitforConnect(int)’:
BemusedServerDlg.cpp:1889: error: ‘bdaddr_t’ was not declared in this scope
BemusedServerDlg.cpp:1889: error: expected `;' before ‘ba’
BemusedServerDlg.cpp:1890: error: aggregate ‘sockaddr_rc rem_addr’ has incomplete type and cannot be defined
BemusedServerDlg.cpp:1919: error: ‘ba’ was not declared in this scope
BemusedServerDlg.cpp:1919: error: ‘baswap’ was not declared in this scope
BemusedServerDlg.cpp:1923: error: ‘batostr’ was not declared in this scope
make: *** [bemusedlinuxserver] Error 1
rado@ubuntu:~/bemusedlinuxserver1.73$ sudo gedit /etc/bemused.conf



```
Any ideas WTF is this?

EDIT: Dont worry it works with Nokia N70 i missed one lib and thats why it didnt work.

---

### Post by cronholio on 2006-10-25
@tobbworld: Try this:

```
sudo apt-get install libgtk2.0-dev
sudo make install
```

Dann sollte es klappen. ;)

---

### Post by tobbworld on 2006-10-25
hi cronholio,

thanks a lot :) it´s the solution.

I found an other solution too, bluemote.
But I can´t pairing my handy (sony k750i) with kubuntu. 
If I send data from/to the pc all works fine.
But I haven´t a connection all the time, only if I send data.

I wrote an entry in /etc/bluetooth for the rfcomm and add my pc as device at my mobile, but there is no constantly connection :(

Any idea?

Thanks a lot.

Tobbe

---

### Post by SIZABANTU on 2006-11-24
Hi im also trying to install bemused but i get this erorr root@timo901-desktop:/home/timo901/Desktop/bemusedlinuxserver1.73# sudo make install
g++ - o bemusedlinuxserver -I/usr/include/xmms -I./ (LIB) `gtk-config --libs --cflags`- fpermissive main.cpp BemusedServerDlg.cpp
/bin/sh: -c: line 0: syntax error near unexpected token `('
/bin/sh: -c: line 0: `g++ - o bemusedlinuxserver -I/usr/include/xmms -I./ (LIB) `gtk-config --libs --cflags`- fpermissive main.cpp BemusedServerDlg.cpp'
make: *** [bemusedlinuxserver] Error 2

Some one please help me ](*,)

---

### Post by SuperEe on 2007-01-18
I just installed this and was getting

```
./BemusedServerDlg.h:66: error: extra qualification ‘CBemusedServerDlg::’ on member ‘ReadFile’
./BemusedServerDlg.h:67: error: extra qualification ‘CBemusedServerDlg::’ on member ‘ReadFile’
./BemusedServerDlg.h:68: error: extra qualification ‘CBemusedServerDlg::’ on member ‘WriteFile’
./BemusedServerDlg.h:69: error: extra qualification ‘CBemusedServerDlg::’ on member ‘WriteFile’
./BemusedServerDlg.h:70: error: extra qualification ‘CBemusedServerDlg::’ on member ‘GetLastError’
./BemusedServerDlg.h:102: error: extra qualification ‘CBemusedServerDlg::’ on member ‘AddBookmarks’
```

So fixed the header file in the installation directory:

```
nano BemusedServerDlg.h
```

Went down and changed

```
bool CBemusedServerDlg::ReadFile(int handle,char* buffer,int maxbytes,long unsigned int* bytesread,int* bla);
bool CBemusedServerDlg::ReadFile(int handle,unsigned char* buffer,int maxbytes,long unsigned int* bytesread,int* bla);
bool CBemusedServerDlg::WriteFile(int handle, char* buffer,int maxbytes, long unsigned int* byteswritten,int* bla);
bool CBemusedServerDlg::WriteFile(int handle,unsigned char* buffer,int maxbytes, long unsigned int* byteswritten,int* bla);
```

to

```
bool ReadFile(int handle,char* buffer,int maxbytes,long unsigned int* bytesread,int* bla);
bool ReadFile(int handle,unsigned char* buffer,int maxbytes,long unsigned int* bytesread,int* bla);
bool WriteFile(int handle, char* buffer,int maxbytes, long unsigned int* byteswritten,int* bla);
bool WriteFile(int handle,unsigned char* buffer,int maxbytes, long unsigned int* byteswritten,int* bla);
```

and 
```
void CBemusedServerDlg::AddBookmarks(CDirTreeNode* aNode, CDirTreeNode* pNode, bool aRecursive);
```

to

```
void AddBookmarks(CDirTreeNode* aNode, CDirTreeNode* pNode, bool aRecursive);
```

This error is explained here:
[http://wiki.frugalware.org/Extra_qualification_error]("http://wiki.frugalware.org/Extra_qualification_error")

Also make sure you have g++ installed if you want to use the Makefile that came with the tarball.

Got it running great on Nokia 3650 :)

---

### Post by acidu on 2007-03-22
after I modified that file... and make install I still get this


acidu@vaio:~/Desktop/bemusedlinuxserver1.71$ sudo make installg++ -o bemusedlinuxserver -I/usr/include/xmms -I./ -lxmms -lbluetooth `gtk-config --libs --cflags` main.cpp BemusedServerDlg.cpp
BemusedServerDlg.cpp:41:33: error: bluetooth/bluetooth.h: No such file or directory
BemusedServerDlg.cpp:42:30: error: bluetooth/rfcomm.h: No such file or directory
BemusedServerDlg.cpp:138: error: ‘bdaddr_t’ does not name a type
BemusedServerDlg.cpp: In member function ‘void CBemusedServerDlg::ReadBluetoothCommand()’:
BemusedServerDlg.cpp:406: error: ‘GetLastError’ was not declared in this scope
BemusedServerDlg.cpp: In member function ‘void CBemusedServerDlg::ReadDir(char*, CDirTreeNode*, bool)’:
BemusedServerDlg.cpp:517: error: ‘GetLastError’ was not declared in this scope
BemusedServerDlg.cpp: In member function ‘void CBemusedServerDlg::SelectInPlaylist()’:
BemusedServerDlg.cpp:704: error: ‘GetLastError’ was not declared in this scope
BemusedServerDlg.cpp: In member function ‘void CBemusedServerDlg::PlayFile(bool)’:
BemusedServerDlg.cpp:729: error: ‘GetLastError’ was not declared in this scope
BemusedServerDlg.cpp:737: error: ‘GetLastError’ was not declared in this scope
BemusedServerDlg.cpp: In member function ‘void CBemusedServerDlg::GetFileInfo()’:
BemusedServerDlg.cpp:825: error: ‘GetLastError’ was not declared in this scope
BemusedServerDlg.cpp:835: error: ‘GetLastError’ was not declared in this scope
BemusedServerDlg.cpp: In member function ‘void CBemusedServerDlg::DownloadFile()’:
BemusedServerDlg.cpp:881: error: ‘GetLastError’ was not declared in this scope
BemusedServerDlg.cpp:891: error: ‘GetLastError’ was not declared in this scope
BemusedServerDlg.cpp: In member function ‘void CBemusedServerDlg::SetVolume()’:
BemusedServerDlg.cpp:935: error: ‘GetLastError’ was not declared in this scope
BemusedServerDlg.cpp: In member function ‘void CBemusedServerDlg::Shuffle()’:
BemusedServerDlg.cpp:1031: error: ‘GetLastError’ was not declared in this scope
BemusedServerDlg.cpp: In member function ‘void CBemusedServerDlg::Repeat()’:
BemusedServerDlg.cpp:1053: error: ‘GetLastError’ was not declared in this scope
BemusedServerDlg.cpp: In member function ‘void CBemusedServerDlg::WriteListToPhone()’:
BemusedServerDlg.cpp:1104: error: ‘GetLastError’ was not declared in this scope
BemusedServerDlg.cpp:1147: error: ‘GetLastError’ was not declared in this scope
BemusedServerDlg.cpp: In member function ‘void CBemusedServerDlg::WriteDirectoryListToPhone()’:
BemusedServerDlg.cpp:1222: error: ‘GetLastError’ was not declared in this scope
BemusedServerDlg.cpp:1232: error: ‘GetLastError’ was not declared in this scope
BemusedServerDlg.cpp:1251: error: ‘GetLastError’ was not declared in this scope
BemusedServerDlg.cpp:1296: error: ‘GetLastError’ was not declared in this scope
BemusedServerDlg.cpp: In member function ‘int CBemusedServerDlg::BluetoothConnectToSocket(int)’:
BemusedServerDlg.cpp:1567: error: aggregate ‘sockaddr_rc loc_addr’ has incomplete type and cannot be defined
BemusedServerDlg.cpp:1594: error: ‘BTPROTO_RFCOMM’ was not declared in this scope
BemusedServerDlg.cpp:1608: error: ‘bdaddr’ was not declared in this scope
BemusedServerDlg.cpp: In member function ‘int CBemusedServerDlg::BluetoothWaitforConnect(int)’:
BemusedServerDlg.cpp:1662: error: ‘bdaddr_t’ was not declared in this scope
BemusedServerDlg.cpp:1662: error: expected `;' before ‘ba’
BemusedServerDlg.cpp:1663: error: aggregate ‘sockaddr_rc rem_addr’ has incomplete type and cannot be defined
BemusedServerDlg.cpp:1692: error: ‘ba’ was not declared in this scope
BemusedServerDlg.cpp:1692: error: ‘baswap’ was not declared in this scope
BemusedServerDlg.cpp:1696: error: ‘batostr’ was not declared in this scope
BemusedServerDlg.cpp: At global scope:
BemusedServerDlg.cpp:1719: error: no ‘char* CBemusedServerDlg::GetLastError()’ member function declared in class ‘CBemusedServerDlg’
make: *** [bemusedlinuxserver] Error 1


any clue how to make it work?

THX

---

### Post by Hemanti on 2007-05-14
@acidu:

Are you sure you didn't occasionally delete the line below the first changement? It starts with "char*".

@SuperEe:

Wow, I would have never come up with this solution. Thank you so much.

I want to add one change yet so that it works:

Delete in the line below your first four changes the "CBemusedServerDlg::" as well so that it reads
```
   char* GetLastError(); 
```

After having found out that sudo checkinstall doesn't work, I did "sudo mae install" and now it works for me, too. :guitar: 

It jut confuses me that the compiler is not compatible to old sources anymore. Why did the developers do this?

---

### Post by bourke_aubrey on 2007-09-20
Hi Ive got a similar problem on Suse 10.2

Heres the output of my konsole:
Earth:/home/abourke/bemusedlinuxserver1.3 # sudo make install
g++ -o bemusedlinuxserver -I/usr/include/xmms -I./ -lxmms -lbluetooth `gtk-config --libs --cflags` main.cpp BemusedServerDlg.cpp
/bin/sh: gtk-config: command not found
./BemusedServerDlg.h:66: error: extra qualification 'CBemusedServerDlg::' on member 'ReadFile'
./BemusedServerDlg.h:67: error: extra qualification 'CBemusedServerDlg::' on member 'ReadFile'
./BemusedServerDlg.h:68: error: extra qualification 'CBemusedServerDlg::' on member 'WriteFile'
./BemusedServerDlg.h:69: error: extra qualification 'CBemusedServerDlg::' on member 'WriteFile'
./BemusedServerDlg.h:70: error: extra qualification 'CBemusedServerDlg::' on member 'GetLastError'
BemusedServerDlg.cpp:42:22: error: xmmsctrl.h: No such file or directory
./BemusedServerDlg.h:66: error: extra qualification 'CBemusedServerDlg::' on member 'ReadFile'
./BemusedServerDlg.h:67: error: extra qualification 'CBemusedServerDlg::' on member 'ReadFile'
./BemusedServerDlg.h:68: error: extra qualification 'CBemusedServerDlg::' on member 'WriteFile'
./BemusedServerDlg.h:69: error: extra qualification 'CBemusedServerDlg::' on member 'WriteFile'
./BemusedServerDlg.h:70: error: extra qualification 'CBemusedServerDlg::' on member 'GetLastError'
BemusedServerDlg.cpp: In member function 'bool CBemusedServerDlg::OnInitDialog()':
BemusedServerDlg.cpp:110: error: 'xmms_remote_set_main_volume' was not declared in this scope
BemusedServerDlg.cpp: In member function 'bool CBemusedServerDlg::CheckWinamp(const char*)':
BemusedServerDlg.cpp:391: error: 'xmms_remote_is_running' was not declared in this scope
BemusedServerDlg.cpp:400: error: 'xmms_remote_is_running' was not declared in this scope
BemusedServerDlg.cpp: In member function 'void CBemusedServerDlg::WriteInfoToPhone()':
BemusedServerDlg.cpp:414: error: 'xmms_remote_get_playlist_pos' was not declared in this scope
BemusedServerDlg.cpp:414: error: 'xmms_remote_get_playlist_time' was not declared in this scope
BemusedServerDlg.cpp:422: error: 'xmms_remote_is_playing' was not declared in this scope
BemusedServerDlg.cpp:423: error: 'xmms_remote_is_paused' was not declared in this scope
BemusedServerDlg.cpp:426: error: 'xmms_remote_get_output_time' was not declared in this scope
BemusedServerDlg.cpp:432: error: 'xmms_remote_is_repeat' was not declared in this scope
BemusedServerDlg.cpp:433: error: 'xmms_remote_is_shuffle' was not declared in this scope
BemusedServerDlg.cpp:440: error: 'xmms_remote_get_playlist_pos' was not declared in this scope
BemusedServerDlg.cpp:440: error: 'xmms_remote_get_playlist_title' was not declared in this scope
BemusedServerDlg.cpp: In member function 'void CBemusedServerDlg::PlayFile(bool)':
BemusedServerDlg.cpp:499: error: 'xmms_remote_playlist_clear' was not declared in this scope
BemusedServerDlg.cpp:503: error: 'GList' was not declared in this scope
BemusedServerDlg.cpp:503: error: 'list' was not declared in this scope
BemusedServerDlg.cpp:504: error: 'gchar' was not declared in this scope
BemusedServerDlg.cpp:504: error: expected primary-expression before ')' token
BemusedServerDlg.cpp:504: error: 'g_strdup' was not declared in this scope
BemusedServerDlg.cpp:504: error: 'g_list_append' was not declared in this scope
BemusedServerDlg.cpp:505: error: 'xmms_remote_playlist_add' was not declared in this scope
BemusedServerDlg.cpp:506: error: 'g_list_free' was not declared in this scope
BemusedServerDlg.cpp:511: error: 'xmms_remote_play' was not declared in this scope
BemusedServerDlg.cpp:523: error: 'xmms_remote_get_playlist_pos' was not declared in this scope
BemusedServerDlg.cpp:523: error: 'xmms_remote_get_playlist_time' was not declared in this scope
BemusedServerDlg.cpp: In member function 'void CBemusedServerDlg::SetVolume()':
BemusedServerDlg.cpp:656: error: 'xmms_remote_set_main_volume' was not declared in this scope
BemusedServerDlg.cpp: In member function 'void CBemusedServerDlg::Play()':
BemusedServerDlg.cpp:663: error: 'xmms_remote_play' was not declared in this scope
BemusedServerDlg.cpp: In member function 'void CBemusedServerDlg::Stop(bool)':
BemusedServerDlg.cpp:670: error: 'xmms_remote_stop' was not declared in this scope
BemusedServerDlg.cpp:672: error: 'xmms_remote_stop' was not declared in this scope
BemusedServerDlg.cpp: In member function 'void CBemusedServerDlg::Pause()':
BemusedServerDlg.cpp:679: error: 'xmms_remote_pause' was not declared in this scope
BemusedServerDlg.cpp: In member function 'void CBemusedServerDlg::NextTrack()':
BemusedServerDlg.cpp:685: error: 'xmms_remote_playlist_next' was not declared in this scope
BemusedServerDlg.cpp:692: error: 'xmms_remote_get_playlist_pos' was not declared in this scope
BemusedServerDlg.cpp:692: error: 'xmms_remote_get_playlist_time' was not declared in this scope
BemusedServerDlg.cpp: In member function 'void CBemusedServerDlg::PreviousTrack()':
BemusedServerDlg.cpp:701: error: 'xmms_remote_playlist_prev' was not declared in this scope
BemusedServerDlg.cpp:708: error: 'xmms_remote_get_playlist_pos' was not declared in this scope
BemusedServerDlg.cpp:708: error: 'xmms_remote_get_playlist_time' was not declared in this scope
BemusedServerDlg.cpp: In member function 'void CBemusedServerDlg::Shuffle()':
BemusedServerDlg.cpp:737: error: 'xmms_remote_is_shuffle' was not declared in this scope
BemusedServerDlg.cpp:737: error: 'xmms_remote_toggle_shuffle' was not declared in this scope
BemusedServerDlg.cpp:740: error: 'xmms_remote_is_shuffle' was not declared in this scope
BemusedServerDlg.cpp:740: error: 'xmms_remote_toggle_shuffle' was not declared in this scope
BemusedServerDlg.cpp: In member function 'void CBemusedServerDlg::Repeat()':
BemusedServerDlg.cpp:759: error: 'xmms_remote_is_repeat' was not declared in this scope
BemusedServerDlg.cpp:759: error: 'xmms_remote_toggle_repeat' was not declared in this scope
BemusedServerDlg.cpp:762: error: 'xmms_remote_is_repeat' was not declared in this scope
BemusedServerDlg.cpp:762: error: 'xmms_remote_toggle_repeat' was not declared in this scope
BemusedServerDlg.cpp: In member function 'void CBemusedServerDlg::Log(char*, ...)':
BemusedServerDlg.cpp:1156: error: 'va_start' was not declared in this scope
BemusedServerDlg.cpp:1158: error: 'va_end' was not declared in this scope
make: *** [bemusedlinuxserver] Error 1
Earth:/home/abourke/bemusedlinuxserver1.3 #     

Any ideas what could be wrong?

---

### Post by bourke_aubrey on 2007-09-20
I tried installing some dev packages, but it looks like the dev package for xmms doesnt exist on the suse 10.2 CD

---

### Post by bourke_aubrey on 2007-09-21
Hi
I have openSuse 10.2. I recently compiled the bemused linux server 1.73. I aslo transfered the client to my nokia 6600 via obex push. When I run bemusedlinuxserver I get this output on the konsole:

Welcome to Bemused 1.73
Copyright Ashley Montanaro 2003
Linux port from Daniel Winter

Warning: No channel defined in config file using default=10
Serial Port service registered
registered SP for channel 10
Message: device: default
Waiting for connection over bluetooth

When I try to connect with the client- it says "searching for devices". Then "No Bluetooth devices found. Try again?"
Anyone have any ideas as to why the blueooth client isnt connecting to the server?

---

