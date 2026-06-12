---
title: "quick question about running XSP for asp.net appliations"
date: 2007-09-01
forum: Programming Talk
---

### Post by triptoe on 2007-09-01
solved it.. i just went to the mono site and downloaded the source for xps then extracted the test directory from it. Not sure why apt-get install xsp never installed this directory.......

hey i have a question.. i am currently testing out using XSP server to host a local page on my computer... however the tutorial i am reading says that i should use the 

/usr/share/doc/xsp/test

directory as the root directory.. for the test pages. The problem is i don't have that directory. I have

/usr/share/doc/mono-doc 

but there is no /test directory for me to test pages. 

The page i wanted to test is this one:
> 
<%@ Page Language="C#" %>  
<script runat="server">  

void Button1_Click(object sender, EventArgs e)  
{  
  titleTag.InnerText = "You clicked the button!";  
}  

void Page_Load(object sender, EventArgs e)  
{  
  if (!IsPostBack)  
    titleTag.InnerText = "Page has loaded";  
}  

</script>  
<html>  
<head>  
<title runat="server" id="titleTag"/>  
</head>  
<body>  
<form runat="server">  
  <asp:Button id="Button1" OnClick="Button1_Click" runat="server" Text="Button"/>  
</form>  
</body>  
</html>

when i run xps from the directory this file is in... i still can't get it to display. So i am wondering.. what should the file be named ? should it be in a folder inside of the root directory named something?

actually wait.. cancel that.. i renamed it to index.html and now it displays this:

> <%@ Page Language="C#" %>

hmm. do i have to create a page with a .aspx extension and link it from the index.html or something?

in other words is there any other way to get this test directory with the sample pages to look at how they work??

---

### Post by emperon on 2007-09-06
just create an aspx file like Default.aspx in any directory you want.

Then run xsp2  in that directory
finally open your browser and type [http://localhost:8080/Default.aspx](http://localhost:8080/Default.aspx)

That's it.

---

