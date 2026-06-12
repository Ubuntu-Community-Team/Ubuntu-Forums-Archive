---
title: "[Python] How to calculate Download Speed?"
date: 2009-10-19
forum: Programming Talk
---

### Post by baskar007 on 2009-10-19
I am new to python,

i want to calculate DownloadSpeed when i download a file using urllib

how can i do this?
help me friends

---

### Post by Habbit on 2009-10-19
Well, you can just time the download. The average download speed is the size of the file divided by the time it took to fetch it. Note that you have to use a large file, large enough that it takes at least 5-10 seconds to download, in order to make sure that the "system" time is small compared to the "network" time.

---

### Post by baskar007 on 2009-10-19
> **Habbit said:**
> Well, you can just time the download. The average download speed is the size of the file divided by the time it took to fetch it. Note that you have to use a large file, large enough that it takes at least 5-10 seconds to download, in order to make sure that the "system" time is small compared to the "network" time.
Thank you.

---

### Post by kavon89 on 2009-10-19
You could also poll the size of the file in bytes every second and find the difference each time if you want to see it in real-time etc.

---

### Post by baskar007 on 2009-10-19
thanks,
is there is any decompiler for ubuntu?
for decompiling *.pyc file

---

### Post by wmcbrine on 2009-10-19
Does anyone actually distribute code as .pyc? Usually you have the .py to look at.

Are you trying to look at some code that calculates download speed, or was that an unrelated question?

---

### Post by baskar007 on 2009-10-20
> **wmcbrine said:**
> Does anyone actually distribute code as .pyc? Usually you have the .py to look at.

Are you trying to look at some code that calculates download speed, or was that an unrelated question?

before 1yr i designed an application for Smartphones, I distributed that app as .pyc 

now i want to look that code for reference. My bad-luck i missed the source code, thats why i asked  decompiler for .pyc

---

### Post by WitchCraft on 2009-10-26
I've stolen it from PHP, converted it to VB.net.
Google for the PHP version (I don't know anymore where I found it), which should be easier to convert to Python than VB.net.


```

Imports Microsoft.VisualBasic

Namespace MyWebsite.ClientInfo

    Public Class cClientInfo

        Public Shared Function GetConnectionSpeed() As Double
            Dim iNumKB As Integer = 512
            Dim dtTime1 As DateTime
            Dim dtTime2 As DateTime
            Dim tsDuration As TimeSpan
            Dim iLength As Integer = 0
            Dim strCheckLen As String = "\n"
            Dim strSpeedTest As String = ""
            'Response.Flush()
            HttpContext.Current.Response.Flush()
            dtTime1 = DateTime.Now
            iLength = strCheckLen.Length

            Dim iIndex As Integer
            For iIndex = 0 To iNumKB - 1 Step iIndex + 1
                strSpeedTest += "".PadRight(1024 - iLength, "/*\\*"(0)) + "\n"
                'Response.Flush()
                HttpContext.Current.Response.Flush()
            Next

            dtTime2 = DateTime.Now
            tsDuration = (dtTime2 - dtTime1)

            Dim dDeltaT As Double = iNumKB / tsDuration.TotalSeconds
            Dim dSpeed As Double = System.Math.Round(dDeltaT, 3)
            strSpeedTest = ""
            Return dSpeed
        End Function

    End Class

End Namespace


```

---

