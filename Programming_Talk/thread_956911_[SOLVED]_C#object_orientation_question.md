---
title: "[SOLVED] C#/object orientation question"
date: 2008-10-23
forum: Programming Talk
---

### Post by beno1990 on 2008-10-23
Hello! I'm a programmer coming from a mostly procedural programming background but I'm learning C# as I go in MonoDevelop.

But there's one thing I can't seem to get and it's bugging me, is if I want to control a window other than the active window. For example, a dialog box popup which asks you to confirm that you want to continue. If I want the dialog box *and* the parent window to close when I click ok, I can't seem to access the parent window, eg:

```

protected virtual void btnOk_clicked (object sender, System.EventArgs e)
{
	MainWindow.Destroy(); //doesn't work
	this.Destroy(); //works fine
}

```

Is there a way to control another class like that which I don't know of?

Thanks for reading this.

---

### Post by jimi_hendrix on 2008-10-23
this closes both (and ends the app)

```
private void button1_Click(object sender, EventArgs e)
        {
            if (MessageBox.Show("hello") == DialogResult.OK)
            {
                Application.Exit();
            }

        }
```

---

### Post by beno1990 on 2008-10-23
Thanks, but I'm not trying to close the application. I still want a dialog box to show with the results of the application's run and give the option of starting from scratch.

---

### Post by jimi_hendrix on 2008-10-23
```
 if (MessageBox.Show("hello") == DialogResult.OK)
            {
                this.Close();
                loadprogram(); //user defined method to load new forum that you make
            }
```

this will close the current forum and then you can load your starting screen with loadprogram method

---

