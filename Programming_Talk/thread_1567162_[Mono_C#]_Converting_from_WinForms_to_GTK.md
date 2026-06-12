---
title: "[Mono C#] Converting from WinForms to GTK"
date: 2010-09-03
forum: Programming Talk
---

### Post by alket on 2010-09-03
I'm trying to convert an application from Windows Forms to GTK, but I cannot convert "this.Invoke".

```
strLocal.Write(downBuffer, 0, bytesSize);
                        // Invoke the method that updates the form's label and progress bar
                        this.Invoke(new UpdateProgessCallback(this.UpdateProgress), new object[] { strLocal.Length, fileSize });
```

---

