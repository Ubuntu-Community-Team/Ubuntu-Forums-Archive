---
title: "send keystrokes to application in linux?"
date: 2012-09-19
forum: Programming Talk
---

### Post by conradin on 2012-09-19
Hi all, 
In the windoze, there is vbs, which has some functions for grabbing an window, and sending keystrokes (appActivate, and sendkeys).

Is there a linux equivalent to perform such a task? 
I would like to send keystokes to things like flash games, and other non-terminal applications. 



a vbs example:
```

'Start vmd, autolog steps.
'VMD can play log files back using the play" or source" commands.
'name files VMDLog_<year-date><time>
Dim ws, strDate, ctime, yr
ctime = Right("00" & Hour(now), 2) & Right("00" & Minute(now), 2) & Right("00" & Second(now), 2)
Set ws=CreateObject("WScript.Shell")
'strDate = Year(Now) & "-" & Right("0" & Month(Now),2) & "-" & Right("0" & Day(Now),2)
yr = Year(Now) & "-" & Right("0" & Month(Now),2) & "-" & Right("0" & Day(Now),2)
'broke it up cuz it was long...
strDate = yr & ctime

ws.run "VMD\vmd.exe", 1, false
'ws.AppActivate("VMD.exe") gets the window with vmd.exe in it
'5000=5secinds for load time
Do Until ws.AppActivate("VMD.exe")
     Wscript.Sleep 5000
Loop

If ws.AppActivate("VMD 1") Then
     ws.SendKeys "log VMDLOG_" & strDate
     Wscript.Sleep 100
     ws.SendKeys "{ENTER}"
Else
     MsgBox "Fatal(ish) error: VMD seems to have suddenly died!"
End If
```

---

### Post by cmont899 on 2012-09-19
The command you are looking for is xdotool

```
 sudo apt-get install xdotool
```

---

