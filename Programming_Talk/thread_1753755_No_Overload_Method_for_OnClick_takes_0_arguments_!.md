---
title: "No Overload Method for OnClick takes 0 arguments !"
date: 2011-05-09
forum: Programming Talk
---

### Post by etdsbastar on 2011-05-09
Hello there,

Please anybody check the below given code and tell me where I am wrong. This is a C# code using system.windows.forms in MonoDevelop.

```
using System;
using System.Drawing;
using System.Windows.Forms;

[assembly: System.Reflection.AssemblyVersion("1.1")]

namespace MyNameSpace {
    public class MyForm : Form {
        private Button btnLoad;
        private PictureBox pBoxPhoto;
        
        public MyForm() 
        {
            btnLoad = new Button();
            btnLoad.Text = "&Load";
            btnLoad.Left = (this.Width - btnLoad.Width)/2;
            btnLoad.Top = 10;
            btnLoad.Click += new EventHandler(this.OnClick());
            
            pBoxPhoto = new PictureBox();
            pBoxPhoto.BorderStyle = BorderStyle.FixedSingle;
            pBoxPhoto.Width = this.Width/2;
            pBoxPhoto.Height = this.Height/2;
            pBoxPhoto.Left = (this.Width - pBoxPhoto.Width) / 2;
            pBoxPhoto.Top = (this.Height - pBoxPhoto.Height) / 2;
            pBoxPhoto.SizeMode = PictureBoxSizeMode.StretchImage;
            
            this.Controls.Add(btnLoad);
            this.Controls.Add(pBoxPhoto);
        }
        
        //private void 
        
        public static void Main() {
            Application.Run(new MyForm());
        }
    }
}
```

---

### Post by MadCow108 on 2011-05-09
you have not Implemented an onclick and you must not use () to set up the delegate:
```
        public void OnClick(object sender,EventArgs e)  
        {
          System.Console.WriteLine("click");
        }
        public MyForm() 
        { 
...
                btnLoad.Click += new EventHandler(this.OnClick)
```

---

### Post by etdsbastar on 2011-05-09
Thank you very much dear. I solved my problem.

---

