---
title: "HOWTO: Install ASP.NET and PHP side by site"
date: 2008-10-30
forum: Outdated Tutorials &amp; Tips
---

### Post by directhex on 2008-10-30
Apparently, this info is required.

Firstly, if you're on Hardy, YOU'RE IN TROUBLE. Due to packaging errors, you can't "just" get Apache to serve both types of file at once. You have three options:

[LIST=1]
[*]Upgrade to Intrepid, follow Intrepid instructions below
[*]Use a third party repo like [http://directhex.mfgames.com/hardy.html](http://directhex.mfgames.com/hardy.html), follow Intrepid instructions below
[*]Use XSP on a different port to Apache, and configure Apache to forward certain requests to XSP (instructions to be posted later, depending on my mood)
[/LIST]

Okay. First, we get PHP working. Install the "libapache2-mod-php5" package in Synaptic. It'll pull in the dependencies. Restart apache to be sure it's working ("/etc/init.d/apache2 restart").

Let's test it. Run "sudo nano /var/www/hello.php" in a console, and paste in the following:

```
<?php
echo "Hello World!";
?>
```

Now, check you can access your new page. From a web browser, try going to [http://127.0.0.1/hello.php](http://127.0.0.1/hello.php). It ought to load up fine:

```
jms@virtman:~$ curl http://http://127.0.0.1/hello.php
Hello World!
jms@virtman:~$
```

Next, ASP.NET. We need to install the "libapache2-mod-mono" AND "mono-apache-server2" packages (if you don't specify the second one, you only get ASP.NET 1.0). If you use Synaptic, be sure to select the second package FIRST, otherwise Synaptic can get confused about dependencies. On systems where Apache isn't correctly configured, this package install can hang - hit ctrl-C in the terminal, and it should recover gracefully.

Now, you can either worry about setting up ASP.NET sites on their own by hand, or not bother & just rely on autoconfig. The former is the default. To change it, run "a2dismod mod_mono; a2enmod mod_mono_auto"

Unfortunately, there's one small problem to fix - mod_mono_auto is hard-coded to try and run "mod-mono-server", but because we're using ASP.NET 2.0, we only have "mod-mono-server2". Place a link manually: "ln -s /usr/bin/mod-mono-server2 /usr/bin/mod-mono-server" - and restart apache.

Finally, try a hello world:
```
<% HelloWorldLabel.Text = "Hello World!"; %>
<html>
  <body>
    <form id="form1" runat="server">
      <asp:Label runat="server" id="HelloWorldLabel" />
    </form>
  </body>
</html>
```

Try hitting [http://127.0.0.1/hello.aspx](http://127.0.0.1/hello.aspx) now, and it should look identical to the (still-functional) PHP example.

```
jms@virtman:~$ curl http://127.0.0.1/hello.aspx

<html>
<body>
    <form method="post" action="hello.aspx" id="form1">
<script type="text/javascript">
//<![CDATA[
        var theForm;
        if (document.getElementById) {theForm = document.getElementById ('form1'); }
        else { theForm = document.form1; }
//]]>
</script>
<div>
        <input type="hidden" name="__VIEWSTATE" id="__VIEWSTATE" value="DAAAAA==" />

</div>
        <span id="HelloWorldLabel">Hello World!</span>
    </form>
</body>
</html>

jms@virtman:~$
```

---

