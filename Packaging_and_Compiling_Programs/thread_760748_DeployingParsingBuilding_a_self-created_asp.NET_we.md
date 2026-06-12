---
title: "Deploying/Parsing/Building a self-created asp.NET website"
date: 2008-04-20
forum: Packaging and Compiling Programs
---

### Post by charlemagne_ishu on 2008-04-20
Hi,
Ive been reading for hours and can't find any solution to my problem:

I've developed a website using ASP.NET with C# code-behind files using VS 2005 on windows....

I want to view the webpages on mozilla in my ubuntu box...for that I have xsp installed (and mono too if that helps)...

the xsp server starts fine with display: (although I get error when trying to view the asp.net2 demo files

```
Listening on port: 8080 (non-secure)
Listening on address: 0.0.0.0
Root directory: /home/charlie/Desktop/pro
Hit Return to stop the server.

```


error for demo files :

```
Description: Error parsing a resource required to service this request. Review your source file and modify it to fix this error.

Error message:

Type not found.

File name: /usr/share/asp.net2-demos/index.aspx

    Line: 59
Source Error:

<td>Here are some ASP.NET examples:

<form id="form1" runat="server">
    <asp:TreeView style="margin:10px" ID="TreeView1" Runat="server"
        EnableClientScript="true"
        PopulateNodesFromClient="false"  
        ExpandDepth="1"
        >
     </asp:TreeView>
</form>
</td>

```

OK, back to the problem....when i try to view my developed webpages I get the following error:
```

Description: Error parsing a resource required to service this request. Review your source file and modify it to fix this error.

Error message:

Cannot find type _Default

File name: /home/charlie/Desktop/pro/Default.aspx

    Line: 1
Source Error:

<%@ Page Language="C#" AutoEventWireup="true"  CodeFile="Default.aspx.cs" Inherits="_Default"%>

<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Transitional//EN" "http://www.w3.org/TR/xhtml1/DTD/xhtml1-transitional.dtd">
```


Somebody please help!!!!

---

### Post by piagent on 2008-12-24
You need to start xsp2 vs xsp if your code is using things like treeView.  I'm just starting on this my self. I got the xsp2 working standalone but my focus is server2 behind apache2 and not without a few problems like:

1) mod mono server2 for apache fails to come up at boot up but does after an apache2 restart.  The error log show an exe format error, can't fine it yet. But I also get the same problem with mod mono server.
2) net2-demos work from alias samples but will not from my var/www folder.

but all and all it is a start.

---

