---
title: "MySql as Registered Data Provider"
date: 2009-03-31
forum: Programming Talk
---

### Post by NiceCup OfTea on 2009-03-31
Hi all,

I have a problem which I just can't find the answer to by searching - yet I'm sure I can't be the first to encounter this.

I'm using MonoDevelop, C# and MySql to develop a small database app. and I'm trying to test my data access 'dll' using Nunit.

I have set up a separate test project and written my tests but I get an error when my tested routine tries to access MySql.

The error is:

Failed to find or load the registered .Net Framework Data Provider 'MySql.Data.MySqlClient'

I'm not sure how much info you guys might need to help with this so I'll keep it simple for now and can provide more info if required.

Thanks

John

---

### Post by Arndt on 2009-03-31
> **NiceCup OfTea said:**
> Hi all,

I have a problem which I just can't find the answer to by searching - yet I'm sure I can't be the first to encounter this.

I'm using MonoDevelop, C# and MySql to develop a small database app. and I'm trying to test my data access 'dll' using Nunit.

I have set up a separate test project and written my tests but I get an error when my tested routine tries to access MySql.

The error is:

Failed to find or load the registered .Net Framework Data Provider 'MySql.Data.MySqlClient'

I'm not sure how much info you guys might need to help with this so I'll keep it simple for now and can provide more info if required.

Thanks

John

When I search for the very error string you show above, Google returns some hits that seem helpful. I can't say if they are, and maybe you tried them already.

---

### Post by NiceCup OfTea on 2009-03-31
Arndt,

I've looked at those but they all talk about web.config and machine.config for ASP apps.  I don't even have an app.config yet 'cos I don't yet have a front end executable of any kind.  

I've tried making a DataAccess.dll.config but that doesn't work and I had no reason to think it should but you have to try everything.  I also tried doing something similar for my test project - but that is also merely a library.  I'm not sure that you can write a config file for a dll - maybe someone can tell me if that is possible?

So I'm a bit confused over what/where I should be putting the information to make MySql a registered provider for the ProviderFactory class.

this link [http://www.mono-project.com/BaseClass_Provider_Factory](http://www.mono-project.com/BaseClass_Provider_Factory) hints at something I could try adding MySql info to BUT I still don't know which config file where.

I'm still no nearer to working this out but maybe the extra info above helps?

Thanks

John

---

