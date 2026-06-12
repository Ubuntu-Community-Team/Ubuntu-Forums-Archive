---
title: "Problems using SSL in C#"
date: 2011-09-10
forum: Programming Talk
---

### Post by Zeikcied on 2011-09-10
Since my last thread, I've discovered that SSL in C# doesn't really require anything more than the normal HTTP stuff.  But now I'm stuck on a completely separate thing.

I can't seem to get Mono to work with the SSL certificates.  No matter what I try, I keep getting an "invalid certificate received from server" error.  Even when testing with [https://encrypted.google.com/](https://encrypted.google.com/) I get the error.  I also got it when using examples on the Mono website ([http://www.mono-project.com/UsingTrustedRootsRespectfully](http://www.mono-project.com/UsingTrustedRootsRespectfully) oddly the .NET 2.0 profile code for Method #-1 doesn't compile, and the .NET 1.0 profile code complains of an obsolete class).

Here's what it shows in the terminal:
```
Unhandled Exception: System.Net.WebException: Error getting response stream (Write: The authentication or decryption has failed.): SendFailure ---> System.IO.IOException: The authentication or decryption has failed. ---> Mono.Security.Protocol.Tls.TlsException: Invalid certificate received from server. Error code: 0xffffffff800b010a
  at Mono.Security.Protocol.Tls.Handshake.Client.TlsServerCertificate.validateCertificates (Mono.Security.X509.X509CertificateCollection certificates) [0x00000] in <filename unknown>:0 
  at Mono.Security.Protocol.Tls.Handshake.Client.TlsServerCertificate.ProcessAsTls1 () [0x00000] in <filename unknown>:0 
  at Mono.Security.Protocol.Tls.Handshake.HandshakeMessage.Process () [0x00000] in <filename unknown>:0 
  at (wrapper remoting-invoke-with-check) Mono.Security.Protocol.Tls.Handshake.HandshakeMessage:Process ()
  at Mono.Security.Protocol.Tls.ClientRecordProtocol.ProcessHandshakeMessage (Mono.Security.Protocol.Tls.TlsStream handMsg) [0x00000] in <filename unknown>:0 
  at Mono.Security.Protocol.Tls.RecordProtocol.InternalReceiveRecordCallback (IAsyncResult asyncResult) [0x00000] in <filename unknown>:0 
  --- End of inner exception stack trace ---
  at Mono.Security.Protocol.Tls.SslStreamBase.AsyncHandshakeCallback (IAsyncResult asyncResult) [0x00000] in <filename unknown>:0 
  --- End of inner exception stack trace ---
  at System.Net.HttpWebRequest.EndGetResponse (IAsyncResult asyncResult) [0x00000] in <filename unknown>:0 
  at System.Net.HttpWebRequest.GetResponse () [0x00000] in <filename unknown>:0 
  at test2.MainClass.Main (System.String[] args) [0x00000] in <filename unknown>:0
```

And this is the actual code (it's example code a friend gave, slightly edited):
```
using System;
using System.Net;
using System.IO;


namespace test2
{
	class MainClass
	{
		public static void Main (string[] args)
		{
try {
	WebRequest request = HttpWebRequest.Create("https://encrypted.google.com/");
    HttpWebResponse response = (HttpWebResponse) request.GetResponse();
    Stream stream = response.GetResponseStream();
}
catch(IOException e) { Console.WriteLine("Failed to connect to URI"); }
catch(UriFormatException e) { Console.WriteLine("Bad URI format"); }
		}
	}
}
```

---

### Post by WitchCraft on 2011-09-10
I had a similar problem.

You should anyway ignore SSL certificate errors.
Because for example when you connect via localhost instead of IP to a server that requires HTTPS, you'll always get this exception.


VB.NET
```

System.Net.ServicePointManager.ServerCertificateValidationCallback = Function() True 

```

C#
```

System.Net.ServicePointManager.ServerCertificateValidationCallback = () => true;

```


See my post here:
[http://stackoverflow.com/questions/3787386/howto-ignore-ssl-certificate-error-in-webservice-request](http://stackoverflow.com/questions/3787386/howto-ignore-ssl-certificate-error-in-webservice-request)

What version of mono are you using anyway ?
Because versions prior to .NET 3.5 didn't correctly handle SSL...

Maybe you should take a look at mono 2.10.4 or 2.11
The 2.6 or 2.8 versions of ubuntu are just annoying, but Ubuntu can't upgrade it without a distro-upgrade, because Banshee et  all require this version, and need to be updated before they can put 2.10 on Ubuntu.

Maybe in the future they'll learn to configure default-mono as parallel install, so one can upgrade the application level mono version without modifying the distro-level version.

In mono 2.11, NuGet will start to work (a first successful attempt)!

---

### Post by WitchCraft on 2011-09-10
Just tested.
I got the exception as well, on 2.10...


But it works like this:

```

using System;
using System.Security.Cryptography.X509Certificates;


namespace SSLtest
{
	
	class MainClass
	{
		
		// callback used to validate the certificate in an SSL conversation
		private static bool ValidateRemoteCertificate(
			object sender,
			X509Certificate certificate,
			X509Chain chain,
			System.Net.Security.SslPolicyErrors policyErrors
		)
		{
			
			return true;
			/*
			if (Convert.ToBoolean(ConfigurationManager.AppSettings["IgnoreSslErrors"]))
			{
				// allow any old dodgy certificate...
				return true;
			}
			else
			{
				return policyErrors == SslPolicyErrors.None;
			}
			*/
		} // End Function ValidateRemoteCertificate

		
		public static void Main (string[] args)
		{
			//System.Net.ServicePointManager.ServerCertificateValidationCallback += ValidateRemoteCertificate;
			System.Net.ServicePointManager.ServerCertificateValidationCallback += (s,ce,ca,p) => true;
			
			string strResponse = null;
			try 
			{
				System.Net.WebRequest request = System.Net.HttpWebRequest.Create("https://encrypted.google.com/");
				System.Net.HttpWebResponse response = (System.Net.HttpWebResponse) request.GetResponse();
				System.IO.Stream stream = response.GetResponseStream();
				System.IO.StreamReader sr = new System.IO.StreamReader(stream);
				strResponse = sr.ReadToEnd();
				sr.Close();
				sr.Dispose();
				stream.Dispose();
			}
			catch(System.IO.IOException ex) 
			{ 
				Console.WriteLine("Failed to connect to URI"); 
				Console.WriteLine("Reason:"); 
				Console.WriteLine(ex.Message);
				Console.WriteLine(Environment.NewLine);
				Console.WriteLine("Stacktrace:"); 
				Console.WriteLine(ex.StackTrace); 
			}
			catch(System.UriFormatException ex) 
			{ 
				Console.WriteLine("Bad URI format"); 
				
				Console.WriteLine("Reason:"); 
				Console.WriteLine(ex.Message); 
				Console.WriteLine(Environment.NewLine);
				Console.WriteLine("Stacktrace:"); 
				Console.WriteLine(ex.StackTrace); 
			}
		
			Console.WriteLine ("Read the following stream:");
			Console.WriteLine(strResponse);
			Console.WriteLine(Environment.NewLine);
			Console.WriteLine(" --- Press any key to continue --- ");
			Console.ReadKey();
		} // End Sub Main 
		
		
	} // End Class MainClass
	
	
} // End Namespace SSLtest

```


As a sidenote:
```

System.Net.ServicePointManager.ServerCertificateValidationCallback = () => true;

```
doesn't compile. Bad advice.

I don't know whether this is the same on Windows, I just know that the VB.NET version works on Windows, and that I used the developer fusion web-service to translate the VB.NET piece to C#.

But it works like this:
```

System.Net.ServicePointManager.ServerCertificateValidationCallback += (s,ce,ca,p) => true;

```

---

### Post by WitchCraft on 2011-09-10
Oh, and BTW:
You better add a 
```

catch(System.Exception ex) 

```

as well, or else your app get's an unhandled exception sooner or later. 
Usually sooner.

---

### Post by Zeikcied on 2011-09-10
Yeah, I have Mono 2.6.7, the version that's in the Ubuntu repositories for 11.04.  I'm running Kubuntu, though, so I don't think Mono is installed or required by default, so the fact that the version is apparently restricted by GTK apps I don't have is a little annoying.

With another site I was trying, I used "certmgr -ssl [website]" to download and install the certificates.  And while that also complained that they're invalid, it seemingly installed them.  But the code still crashes when trying to connect to that site.

I do have a Windows XP virtual machine, so I probably would have better luck writing the code in there, but I suppose it would cause problems if I ran it in Mono.

I would hope that Kubuntu 11.10 would have a more updated Mono.  Would a more recent Mono be able to handle this without any problems?  Or would I still need to ignore the errors and all that?  I would rather wait for a more updated version of Mono that fixes the problem rather than creating a mess of code that just sort of ignores the issue.

---

### Post by WitchCraft on 2011-09-11
> **Zeikcied said:**
> Yeah, I have Mono 2.6.7, the version that's in the Ubuntu repositories for 11.04.  I'm running Kubuntu, though, so I don't think Mono is installed or required by default, so the fact that the version is apparently restricted by GTK apps I don't have is a little annoying.

With another site I was trying, I used "certmgr -ssl [website]" to download and install the certificates.  And while that also complained that they're invalid, it seemingly installed them.  But the code still crashes when trying to connect to that site.

I do have a Windows XP virtual machine, so I probably would have better luck writing the code in there, but I suppose it would cause problems if I ran it in Mono.

I would hope that Kubuntu 11.10 would have a more updated Mono.  Would a more recent Mono be able to handle this without any problems?  Or would I still need to ignore the errors and all that?  I would rather wait for a more updated version of Mono that fixes the problem rather than creating a mess of code that just sort of ignores the issue.

I compiled my latest code with MonoDevelop on Ubuntu, and it downloaded the site's HTML page just fine. But you have to include the CertificateValidationCallback --> true, else it still throws your exception.

---

### Post by directhex on 2011-09-11
> **Zeikcied said:**
> Yeah, I have Mono 2.6.7, the version that's in the Ubuntu repositories for 11.04.  I'm running Kubuntu, though, so I don't think Mono is installed or required by default, so the fact that the version is apparently restricted by GTK apps I don't have is a little annoying.

With another site I was trying, I used "certmgr -ssl [website]" to download and install the certificates.  And while that also complained that they're invalid, it seemingly installed them.  But the code still crashes when trying to connect to that site.

I do have a Windows XP virtual machine, so I probably would have better luck writing the code in there, but I suppose it would cause problems if I ran it in Mono.

I would hope that Kubuntu 11.10 would have a more updated Mono.  Would a more recent Mono be able to handle this without any problems?  Or would I still need to ignore the errors and all that?  I would rather wait for a more updated version of Mono that fixes the problem rather than creating a mess of code that just sort of ignores the issue.

Mono's certificate store is empty, by default.

certmgr is the tool to manage the cert store - and its source code can be used as a reference for managing the cert store inside your app.

certmgr -ssl can be used to add a certificate by trying to connect to a target site and taking its cert. Or you can install a cert individually.

There's also a tool called mozroots, which imports all your Firefox CA certs.

---

### Post by WitchCraft on 2011-09-11
> **directhex said:**
> Mono's certificate store is empty, by default.

certmgr is the tool to manage the cert store - and its source code can be used as a reference for managing the cert store inside your app.

certmgr -ssl can be used to add a certificate by trying to connect to a target site and taking its cert. Or you can install a cert individually.

There's also a tool called mozroots, which imports all your Firefox CA certs.

+1, that's the more correct though more work insentive and less fast way ;-)

But as said, just tell mono's SSL routines to ignore validation errors.
It still transmits encrypted as SSL, just that it doesn't validate the source's authenticity.

---

### Post by Zeikcied on 2011-09-11
> **directhex said:**
> Mono's certificate store is empty, by default.

certmgr is the tool to manage the cert store - and its source code can be used as a reference for managing the cert store inside your app.

certmgr -ssl can be used to add a certificate by trying to connect to a target site and taking its cert. Or you can install a cert individually.

There's also a tool called mozroots, which imports all your Firefox CA certs.

I said I used certmgr -ssl to download and install the certs for another website (it still complained they were invalid but seemed to install them anyway) but the code still threw an exception saying the certificate was invalid.  Even though I had it stored via certmgr.

---

### Post by Zeikcied on 2011-09-11
> **WitchCraft said:**
> I compiled my latest code with MonoDevelop on Ubuntu, and it downloaded the site's HTML page just fine. But you have to include the CertificateValidationCallback --> true, else it still throws your exception.

I only mentioned waiting for the next version of Kubuntu for a hopefully more current Mono because you seemed to imply that newer Mono versions may not have this SSL bug, thus I wouldn't need to ignore any errors.

I guess Oneiric will have Mono 2.10.5, but I don't know if that's better than 2.6.7 in terms of SSL or not.

---

### Post by Dwain.Blazej on 2012-02-29
Run these commands:

```

sudo aptitude install mono-devel
sudo mozroots --import --sync

```

---

### Post by directhex on 2012-02-29
Possible problem is Mono 2.6.7 lacks support for some types of certificate algorithm - we backported a number of cert fixes to the package in Precise for better SSL interop

---

