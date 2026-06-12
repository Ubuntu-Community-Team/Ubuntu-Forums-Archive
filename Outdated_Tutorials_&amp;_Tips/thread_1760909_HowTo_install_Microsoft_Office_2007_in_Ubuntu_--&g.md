---
title: "HowTo install Microsoft Office 2007 in Ubuntu --&gt; wine"
date: 2011-05-17
forum: Outdated Tutorials &amp; Tips
---

### Post by tajlor on 2011-05-17
*[COLOR=#000000][FONT=Arial, sans-serif][SIZE=2]Tested on wine version[/SIZE][/FONT][/COLOR]*[COLOR=#000000][FONT=Arial, sans-serif][SIZE=2]*   1.2.2*
[B]
sudo apt-get install wine
[/B][/SIZE][/FONT][/COLOR] 	 	  **[COLOR=#000000][FONT=Arial, sans-serif][SIZE=2]wget [http://www.kegel.com/wine/winetricks](http://www.kegel.com/wine/winetricks)[/SIZE][/FONT][/COLOR]**


   	 	 	 	 	 	  **[COLOR=#000000][FONT=Arial, sans-serif][SIZE=2]sh winetricks msxml3 dotnet20 gdiplus riched20 riched30 vcrun2005sp1 allfonts[/SIZE][/FONT][/COLOR]**


   	 	 	 	 	 	  [COLOR=#000000][FONT=Arial, sans-serif][SIZE=2]*Microsoft Office 2007 *[/SIZE][/FONT][/COLOR]   	 	 	 	 	 	  [COLOR=#000000] [FONT=Arial, sans-serif][SIZE=2]*requires a libraries, which are not included in a plain Wine-installation. These libraries could be obtained from CrossOver Games, which is a derived version of Wine made to support games under Linux.*[/SIZE][/FONT][/COLOR]


   	 	 	 	 	 	  **[COLOR=#000000] [FONT=Arial, sans-serif][SIZE=2]sudo cp /opt/cxgames/lib/wine/rpcrt4.dll.so .wine/drive_c/windows/system32/[/SIZE][/FONT][/COLOR]**
[COLOR=#000000][FONT=Arial, sans-serif][SIZE=2]
[/SIZE][/FONT][/COLOR]
 
 
 
 
    	 	 	 	 	 	  [COLOR=#000000][FONT=Arial, sans-serif][SIZE=2]*Rename the native Wine-dll version:*[/SIZE][/FONT][/COLOR]
 

 **[COLOR=#000000][FONT=Arial, sans-serif][SIZE=2]sudo mv .wine/drive_c/windows/system32/rpcrt4.dll .wine/drive_c/windows/system32/rpcrt4.dll.bak[/SIZE][/FONT][/COLOR]**
 

 [COLOR=#000000][FONT=Arial, sans-serif][SIZE=2]*Rename CrossOver Games version into the original name:*[/SIZE][/FONT][/COLOR]
 

 [COLOR=#000000] **[FONT=Arial, sans-serif][SIZE=2]sudo mv .wine/drive_c/windows/system32/rpcrt4.dll.so .wine/drive_c/windows/system32/rpcrt4.dll[/SIZE][/FONT]**[/COLOR]


   	 	 	 	 	 	  [FONT=Arial, sans-serif][SIZE=2]*you will need to rename msxml3.dll into *.bak too:*[/SIZE][/FONT]
  
 **[COLOR=#000000] [FONT=Arial, sans-serif][SIZE=2]sudo mv .wine/drive_c/windows/system32/msxml3.dll .wine/drive_c/windows/system32/msxml3.dll.bak[/SIZE][/FONT][/COLOR]**
 
 
  	 	 	 	 	 	  [COLOR=#000000][FONT=Arial, sans-serif][SIZE=2][I]After the renaming it is time to run 
[/I][/SIZE][/FONT][/COLOR]
[COLOR=#000000][FONT=Arial, sans-serif][SIZE=2][/SIZE][/FONT][/COLOR]
**[COLOR=#000000][FONT=Arial, sans-serif][SIZE=2]winecfg[/SIZE][/FONT][/COLOR]**
[COLOR=#000000][FONT=Arial, sans-serif][SIZE=2][/SIZE][/FONT][/COLOR]
[COLOR=#000000][FONT=Arial, sans-serif][SIZE=2][I] again and set msxml3.dll and rpcrt4.dll to “native windows” 
[/I][/SIZE][/FONT][/COLOR]
[COLOR=#000000][FONT=Arial, sans-serif][SIZE=2]*select save and exit.*[/SIZE][/FONT][/COLOR]
 

 [COLOR=#000000][FONT=Arial, sans-serif][SIZE=2]*Now it is time to mount the Office 2007 cd media and start the actual Office 2007 installation.*[/SIZE][/FONT][/COLOR]
 

 **[COLOR=#000000][FONT=Arial, sans-serif][SIZE=2]wine setup.exe[/SIZE][/FONT][/COLOR]**

---

