---
title: "MySql Connector problems with .Net mono"
date: 2010-10-06
forum: Programming Talk
---

### Post by hansoffate on 2010-10-06
I have finally broke down and decided to make a post after 5 hours of troubleshooting and reading forums.  I have setup my apache2 install to use mono by following this guide: [http://ubuntuexperiment.wordpress.com/2009/01/29/running-aspnet-applications-in-ubuntu-using-modmono/](http://ubuntuexperiment.wordpress.com/2009/01/29/running-aspnet-applications-in-ubuntu-using-modmono/)

After I confirmed everything was working, I decided to make a "test" directory to try to make an app that makes a MySql connection.  I found a great tutorial here : [http://townx.org/blog/elliot/using-mysql-asp-net-under-mono-linux](http://townx.org/blog/elliot/using-mysql-asp-net-under-mono-linux) 

I have the 5.2.3.0 MySql connector installed like it said (only difference was I had to use sudo to run the gacutil command).  However, now when I try running the test .aspx page after populating the MySQL DB, I get compilations due to MySqlClient not existing in the namespace.  I believe I have it referenced the correct way.  

Here is the pastebin of the compilation debug from the localhost: 
[http://pastebin.ca/1955414](http://pastebin.ca/1955414)

Any advice on how to correctly reference the MySql.Data.dll file would be great.

Thanks,
-Hans

Web.config file
```

<configuration>
  <system.web>
    <compilation debug="true">
      <assemblies>
        <add assembly="MySql.Data, Version=5.2.3.0, Culture=neutral, PublicKeyToken=C5687FC88969C44D"/>
      </assemblies>
    </compilation>
  </system.web>
</configuration>

```

index.aspx file
```
<%@ Page Language="C#" %>
<%@ Import Namespace="System.Data" %>
<%@ Import Namespace="System.Data.MySqlClient" %>
<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Strict//EN" "http://www.w3.org/TR/xhtml1/DTD/xhtml1-strict.dtd">
<html xmlns="http://www.w3.org/1999/xhtml" xml:lang="en" lang="en">
  <head>
    <title>CD cat</title>
    <meta http-equiv="Content-Type" content="text/html; charset=utf-8" />

    <script runat="server">
    private void Page_Load(Object sender, EventArgs e)
    {
       string connectionString = "Server=localhost;Database=XXXX;User ID=XXXXX;Password=XXXXXXX;Pooling=false;";
       MySqlConnection dbcon = new MySqlConnection(connectionString);
       dbcon.Open();

       MySqlDataAdapter adapter = new MySqlDataAdapter("SELECT * FROM artist", dbcon);
       DataSet ds = new DataSet();
       adapter.Fill(ds, "result");

       dbcon.Close();
       dbcon = null;

       ArtistsControl.DataSource = ds.Tables["result"];
       ArtistsControl.DataBind();
    }
    </script>

  </head>
                         
  <body>
    <h1>Artists</h1>
    <asp:DataGrid runat="server" id="ArtistsControl" />
  </body>

</html>
```

---

### Post by directhex on 2010-10-06
System.Data.MySqlClient is not the same thing as MySql.Data.MySqlClient. The namespace in MySql.Data.dll is MySql.Data.MySqlClient

---

### Post by hansoffate on 2010-10-06
Resolved!

Wow, that was such a simple fix.  I can't believe I misread the namespace/mistyped it.... ::Doh::

Thanks,
-Hans

---

