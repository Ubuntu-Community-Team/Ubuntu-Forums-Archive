---
title: "Strange gcc error"
date: 2009-09-24
forum: Packaging and Compiling Programs
---

### Post by Vanishing on 2009-09-24
I was compiling a simple csharp code, and compiler throws out strange output.
using gcc (up to date with karmic).
code is:
> using System;
using System.Drawing;
using System.IO;
using System.Windows.Forms;

public class MenuDialog : Form {
  TextBox text = new TextBox();

  public MenuDialog() {
    Size = new Size(500,200);

    text.Size = new Size(490,190);
    text.Multiline = true;
    text.ScrollBars = ScrollBars.Both;
    text.WordWrap = false;
    text.Location = new Point(5,5);

    MenuItem fileMenu = new MenuItem("File");
    MenuItem open = new MenuItem("Open");
    open.Shortcut = Shortcut.CtrlO;
    MenuItem save = new MenuItem("Save");
    save.Shortcut = Shortcut.CtrlS;
    fileMenu.MenuItems.Add(open);
    fileMenu.MenuItems.Add(save);

    MenuItem formatMenu = new MenuItem("Format");
    MenuItem font = new MenuItem("Font");
    font.Shortcut = Shortcut.CtrlF;
    formatMenu.MenuItems.Add(font);
     
    MainMenu bar = new MainMenu();
    Menu = bar;
    bar.MenuItems.Add(fileMenu);
    bar.MenuItems.Add(formatMenu);

    Controls.Add(text);

    open.Click += new EventHandler(Open_Click);
    save.Click += new EventHandler(Save_Click);
    font.Click += new EventHandler(Font_Click); 
  }
  
  protected void Open_Click(Object sender, EventArgs e) {
    OpenFileDialog o = new OpenFileDialog();
    if(o.ShowDialog() == DialogResult.OK) {
      Stream file = o.OpenFile();
      StreamReader reader = new StreamReader(file);
      char[] data = new char[file.Length];
      reader.ReadBlock(data,0,(int)file.Length);
      text.Text = new String(data);  
      reader.Close();
    }
  }

  protected void Save_Click(Object sender, EventArgs e) {
    SaveFileDialog s = new SaveFileDialog();
    if(s.ShowDialog() == DialogResult.OK) {
      StreamWriter writer = new StreamWriter(s.OpenFile());
      writer.Write(text.Text);
      writer.Close();
    }
  }
  protected void Font_Click(Object sender, EventArgs e) {
    FontDialog f = new FontDialog();
    if(f.ShowDialog() == DialogResult.OK) 
      text.Font = f.Font;
  }

  public static void Main() {
    Application.Run(new MenuDialog());
  }
}

it is from [http://www.java2s.com/Code/CSharp/GUI-Windows-Form/Asimpletexteditor.htm](http://www.java2s.com/Code/CSharp/GUI-Windows-Form/Asimpletexteditor.htm)

the compiler errors are:
> 
test.c:19: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘System’
test.c:20: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘System’
test.c:21: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘System’
test.c:22: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘System’
test.c:24: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘class’
test.c:92: error: expected identifier or ‘(’ before ‘}’ token
test.c:93: error: expected identifier or ‘(’ before ‘}’ token
test.c:94: error: expected identifier or ‘(’ before ‘}’ token
test.c:95: error: expected identifier or ‘(’ before ‘}’ token
test.c:96: error: expected identifier or ‘(’ before ‘}’ token
test.c:97: error: expected identifier or ‘(’ before ‘}’ token
test.c:98: error: expected identifier or ‘(’ before ‘}’ token
test.c:99: error: expected identifier or ‘(’ before ‘}’ token
using: gcc -c test.c -o test

anyhelp?:confused:

---

### Post by MadCow108 on 2009-09-24
I don't think gcc can compile c# (at least gcc 4.3.3. can't according to man page)
even if it can you must tell it explicitly to do so because from the file extension (.c) it will try to compile it as C code

---

### Post by Vanishing on 2009-09-24
> **MadCow108 said:**
> I don't think gcc can compile c# (at least gcc 4.3.3. can't according to man page)
even if it can you must tell it explicitly to do so because from the file extension (.c) it will try to compile it as C code

yea..i just found that out..:D
now using gmcs..
but i have to assign -r:System..... everytime i compile...is there anyway not to assign it?

---

