---
title: "Gambas: Error with variable"
date: 2008-04-12
forum: Programming Talk
---

### Post by Miles111 on 2008-04-12
Hello,
I am trying to program with Gambas, however several seeming meaningless errors are popping up.
Running my program, I get the error "Syntax error at line 2 in frmLoad.Class". The code is below:
> ' Gambas class file
DIM i AS Integer
i = 0
PUBLIC SUB Form_Open()
  frmLoad.Center
END

PUBLIC SUB Timer1_Timer()
 Progressbar1.Value =  Progressbar1.Value + 0.01
 Number = Progressbar1.Value
 IF Number = "1000" THEN
 frmMain.Load
 frmLoad.Close
 ENDIF
END


---

### Post by kalaharix on 2008-04-13
I am not sure what you are trying to do here. As you have it, you want the progress bar to run and THEN the main form to load. I have made two forms: frmLoad has the progess bar on it. FMain has a textfield and an exit button.
---------------------------------
```
' Gambas class file (FMain.class)

PUBLIC SUB form_Show()
 DIM i AS Integer
  btnExit.Enabled = FALSE
  frmLoad.Show
  FOR i = 1 TO 15
    txtCount.Text = i
    WAIT 0.5
  NEXT 
  btnExit.Enabled = TRUE
END

PUBLIC SUB btnExit_Click()
  fmain.Close
END  
```
---------------------------------
```
' Gambas class file (frmLoad.class)

PUBLIC SUB form_Show()
  DIM i AS Integer
  DIM vlu AS Float
  
  ProgressBar1.Value = 0.0
  FOR i = 1 TO 10
    vlu = i / 10
    ProgressBar1.Value = vlu
    WAIT 1
  NEXT 
  frmLoad.Close
END
```
---------------------------------

I suspect you really want to display the progress bar WHILE the FMain initialises. You would have to put the progress bar on FMain itself and control its display with the .visible attribute.

Hope that helps. You should persevere with Gambas: you won't find anything easier on Linux despite what others say. It uses the same widgets as Python/Glade but is a whole heap more integrated.

rgds

---

