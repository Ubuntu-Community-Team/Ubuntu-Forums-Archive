---
title: "In Gambas, how do you create a .dat file for saving data in a program?"
date: 2009-10-01
forum: Programming Talk
---

### Post by millstone on 2009-10-01
Hello,
In Gamabs, how do you create a .dat file for saving data in a program?
It does not have to be necessarily have to be a .dat file but a file that is saved text from a program. Thanks. Any help much appreciated. :)

EDIT: I found this code online, however It returns an error:
Missing As
Line 2 at Fmain class
Here is the code:
```
' Gambas class file
Option explicit
 CONST AS scombinedfile = "/home/joe/test/combined.dat"
 CONST AS sTmpPix = "/home/joe/test/picxtract.bmp"


PUBLIC SUB _new()

END

PUBLIC SUB Form_Open()

END

PUBLIC SUB Command1_Click()
DIM nImageSize AS Long
DIM hfile AS Long
SavePicture Picture1.Picture, scombinedfile
hFile = FreeFile
OPEN scombinedfile FOR BINARY AS #hFile
nimagesize = Lof(hfile)
SEEK #hFile, nImageSize + 1
Put #hfile,, TextArea.text 

SEEK #hfile, Lof(hfile)
Put #hfile, Lof(hfile) + 1, nimagesize


CLOSE #hfile


END
```

---

### Post by millstone on 2009-10-01
Apparently not alot of people use gambas. :(
I will have to install windows for Visual Basic on my other pc. :(

---

### Post by kalaharix on 2009-10-02
hi,

Here is a sample dragged out of one of my programs. It takes Kerosene sales from 2 POS tills and creates a text file report. The till data selected depends on a radiobutton choice. The first till creates and the second appends.

```

  
  'open the selected file
  WITH $hConn
    .Type = "sqlite3"
    .name = FileChooser1.Value
  END WITH 
  $hConn.Open()
  
  'select the paraffin sales
  sql = "select h_qty,h_date from hist where h_shortdesc='PARAFFIN' and (h_date>='" & Format(Val(txtStartDate.text), "yyyy-mm-dd") & "' and h_date<='" & Format(Val(txtEndDate.text), "yyyy-mm-dd") & "')"
  res = $hConn.Exec(sql)
  
  'if creating the file i.e. first till log
  IF rbutCreate.value = TRUE THEN 
    hFileOut = OPEN User.home & "/paraffin.txt" FOR CREATE
    tot = 0
    cnt = 0
    PRINT #hFileOut, "Paraffin sales from " & txtStartDate.text & " to " & txtEndDate.text
    PRINT #hFileOut, " "
  ELSE 
  'if appending to the file for the second log
    hFileOut = OPEN User.home & "/paraffin.txt" FOR APPEND 
  ENDIF
  
  'create the summary
  FOR EACH res
    tot = tot + res!h_qty
    cnt = cnt + 1
    
    PRINT #hFileOut, res!h_qty, res!h_date
  NEXT
  PRINT #hFileOut, ""
  IF rbutAppend.Value = TRUE THEN 
    PRINT #hFileOut, "Total : " & Format(Str(tot), "###0.0")
    PRINT #hFileOut, "Count : " & Str(cnt)
    SHELL "/usr/bin/lpr paraffin.txt" WAIT 
    #hFileOut.Close
  ENDIF



```

Hope that gives the idea. I know it natural to see the US as the centre of the Universe. Just remember it is the world-wide-web. Some of us are asleep when you post :)

rgds

---

### Post by kalaharix on 2009-10-02
Hi,

Now that I am fully awake :) here is a very simple example. Just 1 button on Form.Main called btnCreate

```

' Gambas class file
PUBLIC lne1 AS String = "This is line 1 of data"
PUBLIC lne2 AS String = "23.54"
PUBLIC hFileOut AS File

PUBLIC SUB btnCreate_Click()
  hFileOut = OPEN User.home & "/test.dat" FOR CREATE
  PRINT #hFileOut, lne1
  PRINT #hFileOut, lne2
  hFileOut.Close
END

```

rgds

---

### Post by millstone on 2009-10-02
Hey thanks very much! I appreciate the code! :)
Btw: Good morning, or should I say Good evening,
(It's still morning in the Us. lol)

---

