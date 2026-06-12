---
title: "C# RichTextBox file IO problems"
date: 2009-03-09
forum: Programming Talk
---

### Post by mulder_edu on 2009-03-09
On the line "tempText.LoadFile(openDocumentDialog.FileName);" in this function, Visual Studio will throw an unhandled exception that the "File format is not valid".  Randomly it works fine, but sometimes it wont take.  Does anyone know why it would do this?  I'm inputing the file name directly from the open dialog.  This is exactly how msdn suggests: [http://msdn.microsoft.com/en-us/library/3f99sst7.aspx](http://msdn.microsoft.com/en-us/library/3f99sst7.aspx)

```
private void openDocument()
{
openDocumentDialog.ShowDialog();
RichTextBox tempText = getTextBox();
tempText.LoadFile(openDocumentDialog.FileName);
}
```

I added an exception handler, and now it just randomly wont load files.  I can try the same file multiple times, and randomly it does or doesn't work.

```
private void openDocument()
{
openDocumentDialog.ShowDialog();
RichTextBox tempText = getTextBox();
try
{
tempText.LoadFile(openDocumentDialog.FileName);
}
catch(ArgumentException e)
{
//Error message
}
}
```

I'm using Visual Studio 2005.

---

