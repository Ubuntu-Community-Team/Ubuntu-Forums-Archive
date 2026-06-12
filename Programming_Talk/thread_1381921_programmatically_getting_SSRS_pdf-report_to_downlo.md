---
title: "programmatically getting SSRS pdf-report to download automatically (on sql-server)"
date: 2010-01-15
forum: Programming Talk
---

### Post by jmejedi on 2010-01-15
..via URL

???????

,,,,,,,,,,,,,,,, easiest way would be ?


{{{{this is what I have so far:

++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
Module Module1

    Sub Main(ByVal args As String())
        Call DownloadFile("http://jme-qr1-sql01/ReportServer$scadareports?%2fConfigurationReport%2fAlarm+Details+Report&OccupancyId=12345&rs:Command=Render&rs:Format=PDF", "C:/\Documents and Settings/\Administrator/\Desktop/\____.pdf", "JME-QR1-SQL01\Administrator", "jimmy1")
        For Each arg As String In args
            Console.WriteLine(arg)
        Next arg
    End Sub

    Sub DownloadFile(ByVal uri As String, ByVal destFile As String, _
Optional ByVal username As String = Nothing, Optional ByVal pwd As String = _
Nothing)
        Dim wc As New System.Net.WebClient
        If Not username Is Nothing AndAlso Not pwd Is Nothing Then
            wc.Credentials = New System.Net.NetworkCredential(username, pwd)
        End If

        wc.DownloadFile(uri, destFile)
    End Sub

End Module
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

,,,,,,,, }}}}


furthermore... To download the output PDF that this SSRS-url returns; automatically, and this being done on the sql-server itself.... it gets to the last line and it encounters runtime-error of "The remote server returned an error: (401) Unauthorized." ....... I believe the issue is how said url is handled within the code, doing it manually works no problem......... any ideas?

Thanks in advance,

J. España

---

### Post by prashantjoshi on 2011-03-09
you need to use 

System.Net.CredentialCache.DefaultNetworkCredentials 

as a credential

try this it works for me.

---

