---
title: "Java HTMLDocument removes whitespace"
date: 2009-04-21
forum: Programming Talk
---

### Post by bostonaholic on 2009-04-21
I've got an issue where I have a JTextPane the user supplies plain text.  When the text is persisted to the DB and brought back to the screen.  Random spaces are being removed.

Here's some code:

In the panel
```
noteTextArea.setContentType("text/html");
HTMLDocument ntaDoc = (HTMLDocument)noteTextArea.getDocument();
ntaDoc.putProperty("IgnoreCharsetDirective", Boolean.TRUE);
ntaDoc.setPreservesUnknownTags(false);
```

In the controller
```
//setting the text of the note 
noteValue.setText(getPanel().noteTextArea.getText());
```

So, the user would type
> Is this note going to have the same problems with the space issues? This is attaching a note through the member profile via Attach > Note.  Let's cross our fingers that this does not happen again.  Please.

And then what's persisted to the DB is a CLOB with the value
> <html>\n  <head>\n\n  </head>\n  <body>\n    <p>\n      Is this note going to have the same problems with the space issues? \n    This is attaching a note through the member profile via Attach &gt; Note. \n  Let's cross our fingers\n that this does not happen again.  Please.    </p>\n  </body>\n</html>\n

When another JPanel reads that from the DB, it comes out to be
> Is this note going to have the same problems with the space **issues?This** is attaching a note through the member profile via Attach > **Note.Let's** cross our fingers that this does not happen again.  Please.

Notice that I bolded where spaces have been removed.

What can I do to fix this?  Thanks.

---

### Post by celthunder on 2009-04-21
I'm not sure how to fix it (sorry have not done java in a few years) but look at where its skipping spaces...at your punctuation..so maybe check for punctuation and add a space after?

---

### Post by bostonaholic on 2009-04-21
> **celthunder said:**
> I'm not sure how to fix it (sorry have not done java in a few years) but look at where its skipping spaces...at your punctuation..so maybe check for punctuation and add a space after?

It was just by coincidence that it's skipping after the punctuation.  Like this example
> Again, we're testing the note length to be sure it is stil removing random spaces. It is believed to happen when this plain text is converted to HTML and in doing this, spaces are removed as newlines, but newlines in HTML result in an empty character.

yeilds this in a separate JPanel
> Again, we're testing the note length to be sure it is stil **removingrandom** spaces. It is believed to happen when this plain text **isconverted** to HTML and in doing this, spaces are removed as newlines, **butnewlines** in HTML result in an empty character.

Thanks.

---

