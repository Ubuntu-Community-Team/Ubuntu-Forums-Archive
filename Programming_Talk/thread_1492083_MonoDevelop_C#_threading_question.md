---
title: "MonoDevelop C# threading question"
date: 2010-05-24
forum: Programming Talk
---

### Post by lexe-cc on 2010-05-24
Hi everyone,

I have a little problem concerning the use of threads to update GTK# widgets which I just can't seem to resolve.

I'm programming a photo managing application using monodevelop in C# & GTK#. Like all other photo managing apps this program has an import function. With large file numbers in mind I tried to use a gtk.progressbar to show the status of the import. The progressbar's text and the bar itself is constantly being updated. 
For the import fuction i'm using a thread to manage this code, so whilst importing a large number of pictures the GUI won't freeze. The thread handles the progressbar update methods as well. 
This works fine as long as the focus stays with the program. From the moment I open another program (so my application loses focus) the progressbar stops updating itself but the importation keeps on going untill it finishes.

I've included a screenshot. I was trying this with an import of 730 files when switching windows. The update process got stuck (see the progressbar in the lower right corner)

The thread is programmed like this:
```
		Thread oThread = new Thread(new ThreadStart(ThreadImport));
		oThread.Start();
```

Also, if I minimize the window and restore it, the window shows up entirely blank. So the gui update freezes involve the whole program.

After a long search on the net I'm starting to feel this "problem" will be easy to resolve. Can anyone shed some light on this?

Thanks in advance!

---

### Post by JwB Zoofware on 2010-05-24
Are you invoking the GUI thread to update the progress bar rather than the worker thread?

i.e, in the worker thread:

Gtk.Application.Invoke(delegate { updateprogress(); });

---

### Post by lexe-cc on 2010-05-24
This is the code I use for the import process. I'm updating the progressbar from within the thread .. I guess this is not the way of doing this?

```

	private void Import()
	{
		Thread oThread = new Thread(new ThreadStart(ThreadImport));
		oThread.Start();
	}
	
	private void ThreadImport()
	{
		int iErrors = 0;
		for (int i = 0; i < arr_sImportFiles.Length; i++) 
		{
			string sResult = oLib.ImportFile(arr_sImportFiles[i], sImportTargetAlbum, sImportMethod);
			if (sResult != "")
			{ 
				Console.WriteLine(sResult);
				iErrors += 1;
			}
			pgbStatus.Text = "Importing files ... (" + i.ToString() + "/" + arr_sImportFiles.Length.ToString() + ")";
			pgbStatus.Fraction = Convert.ToDouble(i) / Convert.ToDouble(arr_sImportFiles.Length);
		}
		pgbStatus.Text = arr_sImportFiles.Length.ToString() + " files imported with " + iErrors.ToString() + " errors.";
		pgbStatus.Fraction = 0.0;
	}

```

I tried to call "Import()" to start the importation
And i tried "Application.Invoke(delegate{Import();});"

It still hangs ..

---

### Post by lexe-cc on 2010-05-24
Ok I got this, I did not use the Application.Invoke correctly :) I've searched for application.invoke and gave me a lot of informaiton on this stuff.
I think the problem is solved now.

Thanks for your help on this!

---

### Post by JwB Zoofware on 2010-05-24
No probs :)

---

