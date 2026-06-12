---
title: "Compilation error with MySql."
date: 2010-02-11
forum: Programming Talk
---

### Post by paul_a_bennett on 2010-02-11
(I've tried to explain the situation at the front so all my questions are at the very end of this post.)

I'm developing a project using Monodevelop 2.0.

I'm trying to access a MySql database through an ObjectDataSource as in:

		[FONT="Courier New"]<asp:ObjectDataSource
		     id="GERDataSource"
		     TypeName="GERDataReader"
		     SelectMethod="GetAllData"
		     runat="server"
		/>[/FONT]

I implemented my GERDataReader as follows:

[FONT="Courier New"]using System;
using System.Data;
using MySql.Data;
using MySql.Data.MySqlClient;
using System.Web.Configuration;

namespace GER2GVODS
{
	
	
	public class GERDataReader
	{
		private readonly string connectionString;
		
		public MySqlDataReader GetAllData ()
		{
			MySqlConnection connection = new MySqlConnection (connectionString);
			connection.Open ();
			MySqlCommand    command    = new MySqlCommand ("select * from Consumption", connection);
            return command.ExecuteReader (CommandBehavior.CloseConnection);
		}
		
		public GERDataReader()
		{
			connectionString = WebConfigurationManager.ConnectionStrings ["GERTestDataSource"].ConnectionString;
		}
	}
}[/FONT]

My web.xml file references the MySql connector:

[FONT="Courier New"]<?xml version="1.0"?>
<!--
Web.config file for GER2GVODS.

The settings that can be used in this file are documented at 
[http://www.mono-project.com/Config_system.web](http://www.mono-project.com/Config_system.web) and 
[http://msdn2.microsoft.com/en-us/library/b5ysx397.aspx](http://msdn2.microsoft.com/en-us/library/b5ysx397.aspx)
-->
<configuration>
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
  <system.data>
    <DbProviderFactories>
      <clear />
      <add name="MySQL Data Provider" invariant="MySql.Data.MySqlClient" description=".Net Framework Data Provider for MySQL" type="MySql.Data.MySqlClient.MySqlClientFactory, MySql.Data, Version=5.2.1.0, Culture=neutral, PublicKeyToken=20449f9ba87f7ae2" />
    </DbProviderFactories>
  </system.data>
  <connectionStrings>
    <remove name="GERTestDataSource" />
    <add name="GERTestDataSource" connectionString="server=secret;user=secret;database=secret;pwd=secret" />
  </connectionStrings>
</configuration>
[/FONT]

I've placed the code into an App_Code directory within the main directory.

Now here's the problem: When I compile everything in monodevelop, everything goes well.  When the page pops up in the web browser, however, there's an error message, as follows:

[FONT="Courier New"]Server Error in '/' Application
Compilation Error

Description: Error compiling a resource required to service this request. Review your source file and modify it to fix this error.

Compiler Error Message: CS0246: The type or namespace name `MySql' could not be found. Are you missing a using directive or an assembly reference?

Source Error:

Line 2: using System;
Line 3: using System.Data;
Line 4: using MySql.Data;
Line 5: using MySql.Data.MySqlClient;
Line 6: using System.Web.Configuration;


Source File: /home/paul/Programming/GER2GVODS/GER2GVODS/App_Code/GERDataReader.cs  Line: 4

Show Detailed Compiler Output:

gmcs /target:library /lib:"/home/paul/Programming/GER2GVODS/GER2GVODS/bin" /debug+ /optimize- /warn:0 /out:"/tmp/paul-temp-aspnet-0/9c9903c9/App_Code.631f391d.dll" /r:"/home/paul/Programming/GER2GVODS/GER2GVODS/bin/GER2GVODS.dll" /r:"/usr/lib/mono/gac/System/2.0.0.0__b77a5c561934e089/System.dll" /r:"/usr/lib/mono/gac/System.Configuration/2.0.0.0__b03f5f7f11d50a3a/System.Configuration.dll" /r:"/usr/lib/mono/gac/System.Data/2.0.0.0__b77a5c561934e089/System.Data.dll" /r:"/usr/lib/mono/gac/System.Drawing/2.0.0.0__b03f5f7f11d50a3a/System.Drawing.dll" /r:"/usr/lib/mono/gac/System.Web/2.0.0.0__b03f5f7f11d50a3a/System.Web.dll" /r:"/usr/lib/mono/gac/System.Web.Services/2.0.0.0__b03f5f7f11d50a3a/System.Web.Services.dll" /r:"/usr/lib/mono/gac/System.Xml/2.0.0.0__b77a5c561934e089/System.Xml.dll" /r:"/usr/lib/mono/gac/System/2.0.0.0__b77a5c561934e089/System.dll" /r:"/usr/lib/mono/gac/System.Configuration/2.0.0.0__b03f5f7f11d50a3a/System.Configuration.dll" /r:"/usr/lib/mono/gac/System.Data/2.0.0.0__b77a5c561934e089/System.Data.dll" /r:"/usr/lib/mono/gac/System.Drawing/2.0.0.0__b03f5f7f11d50a3a/System.Drawing.dll" /r:"/usr/lib/mono/gac/System.Web/2.0.0.0__b03f5f7f11d50a3a/System.Web.dll" /r:"/usr/lib/mono/gac/System.Web.Services/2.0.0.0__b03f5f7f11d50a3a/System.Web.Services.dll" /r:"/usr/lib/mono/gac/System.Xml/2.0.0.0__b77a5c561934e089/System.Xml.dll" /r:"/home/paul/Programming/GER2GVODS/GER2GVODS/bin/GER2GVODS.dll"  /langversion:ISO-2 -- "/tmp/paul-temp-aspnet-0/9c9903c9/App_Web_2c2b4638_1.cs" 

/home/paul/Programming/GER2GVODS/GER2GVODS/App_Code/GERDataReader.cs(4,7): error CS0246: The type or namespace name `MySql' could not be found. Are you missing a using directive or an assembly reference?
/home/paul/Programming/GER2GVODS/GER2GVODS/App_Code/GERDataReader.cs(5,7): error CS0246: The type or namespace name `MySql' could not be found. Are you missing a using directive or an assembly reference?
/home/paul/Programming/GER2GVODS/GER2GVODS/App_Code/GERDataReader.cs(4,7): error CS0246: The type or namespace name `MySql' could not be found. Are you missing a using directive or an assembly reference?
/home/paul/Programming/GER2GVODS/GER2GVODS/App_Code/GERDataReader.cs(5,7): error CS0246: The type or namespace name `MySql' could not be found. Are you missing a using directive or an assembly reference?


Show Complete Compilation Source:

Line 1: 
Line 2: using System;
Line 3: using System.Data;
Line 4: using MySql.Data;
Line 5: using MySql.Data.MySqlClient;
Line 6: using System.Web.Configuration;
Line 7: 
Line 8: namespace GER2GVODS
Line 9: {
Line 10: 	
Line 11: 	
Line 12: 	public class GERDataReader
Line 13: 	{
Line 14: 		private readonly string connectionString;
Line 15: 		
Line 16: 		public MySqlDataReader GetAllData ()
Line 17: 		{
Line 18: 			MySqlConnection connection = new MySqlConnection (connectionString);
Line 19: 			connection.Open ();
Line 20: 			MySqlCommand    command    = new MySqlCommand ("select * from Consumption", connection);
Line 21:             return command.ExecuteReader (CommandBehavior.CloseConnection);
Line 22: 		}
Line 23: 		
Line 24: 		public GERDataReader()
Line 25: 		{
Line 26: 			connectionString = WebConfigurationManager.ConnectionStrings ["GERTestDataSource"].ConnectionString;
Line 27: 		}
Line 28: 	}
Line 29: }[/FONT]

Alternatively, if I place the code in the main directory, I get the following error:

[FONT="Courier New"]Server Error in '/' Application
Type not found: GERDataReader

Description: HTTP 500. Error processing request.

Stack Trace:

System.InvalidOperationException: Type not found: GERDataReader
  at System.Web.UI.WebControls.ObjectDataSourceView.get_ObjectType () [0x00044] in /build/buildd/mono-2.4.2.3+dfsg/mcs/class/System.Web/System.Web.UI.WebControls/ObjectDataSourceView.cs:514 
  at System.Web.UI.WebControls.ObjectDataSourceView.GetObjectMethod (System.String methodName, IOrderedDictionary parameters, DataObjectMethodType methodType) [0x00000] in /build/buildd/mono-2.4.2.3+dfsg/mcs/class/System.Web/System.Web.UI.WebControls/ObjectDataSourceView.cs:839 
  at System.Web.UI.WebControls.ObjectDataSourceView.InvokeSelect (System.String methodName, IOrderedDictionary paramValues) [0x00000] in /build/buildd/mono-2.4.2.3+dfsg/mcs/class/System.Web/System.Web.UI.WebControls/ObjectDataSourceView.cs:791 
  at System.Web.UI.WebControls.ObjectDataSourceView.ExecuteSelect (System.Web.UI.DataSourceSelectArguments arguments) [0x00122] in /build/buildd/mono-2.4.2.3+dfsg/mcs/class/System.Web/System.Web.UI.WebControls/ObjectDataSourceView.cs:732 
  at System.Web.UI.DataSourceView.Select (System.Web.UI.DataSourceSelectArguments selectArgs, System.Web.UI.DataSourceViewSelectCallback callBack) [0x00018] in /build/buildd/mono-2.4.2.3+dfsg/mcs/class/System.Web/System.Web.UI/DataSourceView.cs:149 
  at System.Web.UI.WebControls.DataBoundControl.PerformSelect () [0x00029] in /build/buildd/mono-2.4.2.3+dfsg/mcs/class/System.Web/System.Web.UI.WebControls/DataBoundControl.cs:219 
  at System.Web.UI.WebControls.BaseDataBoundControl.DataBind () [0x00000] in /build/buildd/mono-2.4.2.3+dfsg/mcs/class/System.Web/System.Web.UI.WebControls/BaseDataBoundControl.cs:143 
  at System.Web.UI.WebControls.GridView.DataBind () [0x00012] in /build/buildd/mono-2.4.2.3+dfsg/mcs/class/System.Web/System.Web.UI.WebControls/GridView.cs:1541 
  at System.Web.UI.WebControls.BaseDataBoundControl.EnsureDataBound () [0x00016] in /build/buildd/mono-2.4.2.3+dfsg/mcs/class/System.Web/System.Web.UI.WebControls/BaseDataBoundControl.cs:149 
  at System.Web.UI.WebControls.CompositeDataBoundControl.CreateChildControls () [0x00048] in /build/buildd/mono-2.4.2.3+dfsg/mcs/class/System.Web/System.Web.UI.WebControls/CompositeDataBoundControl.cs:62 
  at System.Web.UI.Control.EnsureChildControls () [0x00041] in /build/buildd/mono-2.4.2.3+dfsg/mcs/class/System.Web/System.Web.UI/Control.cs:757 
  at System.Web.UI.Control.PreRenderRecursiveInternal () [0x00015] in /build/buildd/mono-2.4.2.3+dfsg/mcs/class/System.Web/System.Web.UI/Control.cs:1522 
  at System.Web.UI.Control.PreRenderRecursiveInternal () [0x00072] in /build/buildd/mono-2.4.2.3+dfsg/mcs/class/System.Web/System.Web.UI/Control.cs:1543 
  at System.Web.UI.Control.PreRenderRecursiveInternal () [0x00072] in /build/buildd/mono-2.4.2.3+dfsg/mcs/class/System.Web/System.Web.UI/Control.cs:1543 
  at System.Web.UI.Page.ProcessLoadComplete () [0x00089] in /build/buildd/mono-2.4.2.3+dfsg/mcs/class/System.Web/System.Web.UI/Page.cs:1647 
  at System.Web.UI.Page.InternalProcessRequest () [0x001cb] in /build/buildd/mono-2.4.2.3+dfsg/mcs/class/System.Web/System.Web.UI/Page.cs:1536 
  at System.Web.UI.Page.ProcessRequest (System.Web.HttpContext context) [0x0005b] in /build/buildd/mono-2.4.2.3+dfsg/mcs/class/System.Web/System.Web.UI/Page.cs:1353[/FONT] 

So, my questions:

[LIST=1]
[*]Why can't it find my GERDataReader when it is in the same directory?
[*]What do I have to do in order for it to find GERDataReader?
[*]In the case where the code is in the App_Code directory (which seems neater), why is the reference to the MySql connector in the web.xml file not enough for it to compile correctly?
[*]What do I have to do in order for it to find MySql and compile correctly?
[/LIST]

Your help will be greatly appreciated.

---

