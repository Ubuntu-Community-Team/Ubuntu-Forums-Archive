---
title: "Grief with MySQL connection string and ASP.NET in mono"
date: 2009-09-12
forum: Programming Talk
---

### Post by paul_a_bennett on 2009-09-12
My goal is to create a simple web application using mono.  It is to retrieve data from and store it in a MySql database.

I am running Ubuntu desktop 9.04.

I am using MonoDevelop 2.0.

Among the packages referenced in my project is MySql.Data Version 5.2.1.

gacutil reports as follows:

$ gacutil -l | grep -i my

MySql.Data, Version=5.2.1.0, Culture=neutral, PublicKeyToken=20449f9ba87f7ae2
policy.5.0.MySql.Data, Version=0.0.0.0, Culture=neutral, PublicKeyToken=20449f9ba87f7ae2



My Default.aspx file contains the following code:

	    <asp:SqlDataSource
	         id="CourseSource"   
	         SelectCommand="select id, CourseOffering from Offerings"
	         ConnectionString="<$ ConnectionStrings:TwoHT %>"
	         runat="server"
	    />

My Default.aspx.cs file contains the following lines:

using System;
using System.Web;
using System.Web.UI;
using System.Data;
using MySql.Data;
using MySql.Data.MySqlClient;

My web.config file contains the following lines:

  <connectionStrings>
    <remove name="TwoHT" />
    <add name="TwoHT" connectionString="server=exserver;database=TwoHTSched;uid=paul;pwd=2HT;" />
  </connectionStrings>

(<add name.... is all one one line with ....pwd=2HT;" />

When I use monodevelop's tools/database to access my database, all is well.

However, when I run the application, I get the following output:

Server Error in '/' Application
Format of initialization string does not conform to specifications

Description: HTTP 500. Error processing request.

Stack Trace:

System.ArgumentException: Format of initialization string does not conform to specifications
  at System.Data.SqlClient.SqlConnection.SetConnectionString (System.String connectionString) [0x0029f] in /build/buildd/mono-2.0.1/mcs/class/System.Data/System.Data.SqlClient/SqlConnection.cs:736 
  at System.Data.SqlClient.SqlConnection.set_ConnectionString (System.String value) [0x00017] in /build/buildd/mono-2.0.1/mcs/class/System.Data/System.Data.SqlClient/SqlConnection.cs:163 
  at System.Web.UI.WebControls.SqlDataSourceView.InitConnection () [0x00038] in /build/buildd/mono-2.0.1/mcs/class/System.Web/System.Web.UI.WebControls/SqlDataSourceView.cs:61 
  at System.Web.UI.WebControls.SqlDataSourceView.ExecuteSelect (System.Web.UI.DataSourceSelectArguments arguments) [0x000a2] in /build/buildd/mono-2.0.1/mcs/class/System.Web/System.Web.UI.WebControls/SqlDataSourceView.cs:206 
  at System.Web.UI.WebControls.ListControl.OnDataBinding (System.EventArgs e) [0x00007] in /build/buildd/mono-2.0.1/mcs/class/System.Web/System.Web.UI.WebControls/ListControl.cs:398 
  at System.Web.UI.WebControls.ListControl.PerformSelect () [0x00000] in /build/buildd/mono-2.0.1/mcs/class/System.Web/System.Web.UI.WebControls/ListControl.cs:505 
  at System.Web.UI.WebControls.BaseDataBoundControl.DataBind () [0x00000] in /build/buildd/mono-2.0.1/mcs/class/System.Web/System.Web.UI.WebControls/BaseDataBoundControl.cs:143 
  at System.Web.UI.WebControls.BaseDataBoundControl.EnsureDataBound () [0x00016] in /build/buildd/mono-2.0.1/mcs/class/System.Web/System.Web.UI.WebControls/BaseDataBoundControl.cs:149 
  at System.Web.UI.WebControls.BaseDataBoundControl.OnPreRender (System.EventArgs e) [0x00007] in /build/buildd/mono-2.0.1/mcs/class/System.Web/System.Web.UI.WebControls/BaseDataBoundControl.cs:182 
  at System.Web.UI.WebControls.ListControl.OnPreRender (System.EventArgs e) [0x00000] in /build/buildd/mono-2.0.1/mcs/class/System.Web/System.Web.UI.WebControls/ListControl.cs:411 
  at System.Web.UI.WebControls.ListBox.OnPreRender (System.EventArgs e) [0x00000] in /build/buildd/mono-2.0.1/mcs/class/System.Web/System.Web.UI.WebControls/ListBox.cs:209 
  at System.Web.UI.Control.PreRenderRecursiveInternal () [0x0003b] in /build/buildd/mono-2.0.1/mcs/class/System.Web/System.Web.UI/Control.cs:1509 
  at System.Web.UI.Control.PreRenderRecursiveInternal () [0x00072] in /build/buildd/mono-2.0.1/mcs/class/System.Web/System.Web.UI/Control.cs:1516 
  at System.Web.UI.Control.PreRenderRecursiveInternal () [0x00072] in /build/buildd/mono-2.0.1/mcs/class/System.Web/System.Web.UI/Control.cs:1516 
  at System.Web.UI.Page.ProcessLoadComplete () [0x00089] in /build/buildd/mono-2.0.1/mcs/class/System.Web/System.Web.UI/Page.cs:1635 
  at System.Web.UI.Page.InternalProcessRequest () [0x001cb] in /build/buildd/mono-2.0.1/mcs/class/System.Web/System.Web.UI/Page.cs:1529 
  at System.Web.UI.Page.ProcessRequest (System.Web.HttpContext context) [0x0005b] in /build/buildd/mono-2.0.1/mcs/class/System.Web/System.Web.UI/Page.cs:1343 

Version information: Mono Version: 2.0.50727.42; ASP.NET Version: 2.0.50727.42

My questions:

[LIST]
Why am I getting this message?
[/LIST]
[LIST]
[*]Is the 'initialization string' the error message refers toi the same as the 'connectionString' in my web.config file?
[*]What is the correct format for the string?
[*]Is there some other reason for this error?
[/LIST]

Your help will be greatly appreciated as I've been tearing my hair out over this stupid little problem for altogether too long now.

All the best!

---

### Post by DaithiF on 2009-09-12
Hi,
from looking at this:
[http://www.mono-project.com/MySQL](http://www.mono-project.com/MySQL)

your connection string doesn't look right ... uid, pwd parameters rather than User ID, Password, plus i don't know if the server and database param names are case sensitive or not but I would follow the documentation above, ie. Server=, Database=
connectionString="server=exserver;database=TwoHTSc  hed;uid=paul;pwd=2HT;"

---

### Post by paul_a_bennett on 2009-09-12
Thanks for the suggestion.

I tried changing the connectionString as you suggested (and as per the page you pointed to) but got exactly the same result.

Any other ideas?

---

### Post by paul_a_bennett on 2009-09-13
This problem has taken a few turns since I've last written.

Somehow, I now have it so that it no longer complains of the connectionString.

However, at this point, when I put all the appropriate fields in to connect the application to the MySql database server, mono can't seem to load it into the web server for some reason.  After nearly a minute of waiting, it pops up a window saying 

Error launching web browser

MonoDevelop.Core.UserException: Could not connect to webserver [http://127.0.0.1:8080](http://127.0.0.1:8080) at MonoDevelop.AspNet.Gui.BrowserLauncherOperation.LaunchWebBrowser () [0x00000]

If I strip out the <asp:SqlDataSource stuff from my Default.aspx file, the application runs to the point of complaining that it can't find the SqlDataSource.  When I put the <asp:SqlDataSource stuff back in, the application won't go into the web server.  

For reference, I'm using the following snippets:

         <asp:SqlDataSource
             id="CourseSource"
             ConnectionString="<%$ ConnectionStrings:TwoHT %>"
             SelectCommand="select id, CourseOffering from Offerings"
             Runat="server"
          />

         <asp:SqlDataSource
             id="CourseSource"
             ConnectionString="<%$ ConnectionStrings:TwoHT %>"
             SelectCommand="select id, CourseOffering from Offerings"
             Runat="server"
          />

The following is my web.config file:


<?xml version="1.0"?>
<!--
Web.config file for TwoHTSched.

The settings that can be used in this file are documented at 
[http://www.mono-project.com/Config_system.web](http://www.mono-project.com/Config_system.web) and 
[http://msdn2.microsoft.com/en-us/library/b5ysx397.aspx](http://msdn2.microsoft.com/en-us/library/b5ysx397.aspx)
-->
<configuration>

  <connectionStrings>
    <remove name="TwoHT" />
    <add    name="TwoHT"
            connectionString="Server=exserver;Database=TwoHTSched;Uid=paul;pwd=2HT"
    />
  </connectionStrings>

  <system.web>
    <compilation defaultLanguage="C#" debug="true">
      <assemblies>
        <add assembly="MySql.Data, Version=5.2.1.0, Culture=neutral, PublicKeyToken=20449f9ba87f7ae2" />
      </assemblies>
    </compilation>
    <customErrors mode="RemoteOnly">
    </customErrors>
    <authentication mode="None">
    </authentication>
    <authorization>
      <allow users="*" />
    </authorization>
    <httpHandlers>
    </httpHandlers>
    <trace enabled="false" localOnly="true" pageOutput="false" requestLimit="10" traceMode="SortByTime" />
    <sessionState mode="InProc" cookieless="false" timeout="20" />
    <globalization requestEncoding="utf-8" responseEncoding="utf-8" />
    <pages>
    </pages>
  </system.web>
</configuration>


I am stymied, at this point, and would really appreciate any ideas as to what I might be doing wrong.  I realize this is probably some stupid little configuration issue but, being a newbie to this kind of programming, it's very frustrating to not know where to look or even how to debug this kind of situation. 

Your suggestions will be greatly appreciated.

---

### Post by directhex on 2009-09-13
Can you try installing the package from Debian Unstable, see if it helps? Ta.

---

### Post by paul_a_bennett on 2009-09-13
I'm not quite sure which package you are suggesting that I reinstall.

Are you suggesting that I reinstall mono, monodevelop, mysql, xsp2, or the MySql/Net connector?

Thanks.

---

### Post by directhex on 2009-09-13
> **paul_a_bennett said:**
> I'm not quite sure which package you are suggesting that I reinstall.

Are you suggesting that I reinstall mono, monodevelop, mysql, xsp2, or the MySql/Net connector?

Thanks.

[http://packages.debian.org/sid/libmysql6.0-cil](http://packages.debian.org/sid/libmysql6.0-cil)

---

### Post by paul_a_bennett on 2009-09-14
Thanks for the pointer.

I understand how to remove the existing MySql/Net Connector package.  I am familiar with retrieving packages from the 'standard' ubuntu spots but would appreciate your letting me know how I could download and install the package you've recommended.

---

### Post by directhex on 2009-09-14
> **paul_a_bennett said:**
> Thanks for the pointer.

I understand how to remove the existing MySql/Net Connector package.  I am familiar with retrieving packages from the 'standard' ubuntu spots but would appreciate your letting me know how I could download and install the package you've recommended.

At the bottom under "Download libmysql6.0-cil"

---

### Post by paul_a_bennett on 2009-09-15
Thanks for your suggestion.

However, truth be told, I am loath to try using software which is still considered unstable.

Nonetheless, I have triumphed, overall!

I first tried hand-writing a C# program to access my database and managed to get that working.  Thus, it seemed that it wasn't a matter of the connector.

Next, I tried using an ODBC-based approach.  My attempt to use iODBC failed but with UnixODBC, once I got the connection string working, that worked fine.  For now, that's what I'm going to stick with as I have to get past silly configuration issues and get on with the functionality.

Thanks again for your suggestions.

---

