---
title: "[Java] String.format and JTextPane aren't friends"
date: 2010-09-18
forum: Programming Talk
---

### Post by SpinningAround on 2010-09-18
When I 'print' a formatted string in a JTextPane does it look like Style have no effect. Also I can't get all text to align to left.

When I use this code, will it not get effected by
```

addLogEntry(String.format("%15s:%10s", key, settings.getProperty(key)));

```
```


		StyleConstants.setAlignment(message, StyleConstants.ALIGN_LEFT);

```

[PHP]
private Style message = null, timestamp=null;
private StyledDocument log = null;

		StyleContext context = new StyleContext();
		log = new DefaultStyledDocument(context);
		message = context.getStyle(StyleContext.DEFAULT_STYLE);
		
		StyleConstants.setAlignment(message, StyleConstants.ALIGN_LEFT);
		StyleConstants.setFontSize(message, 10);
		StyleConstants.setSpaceAbove(message, 1);
		StyleConstants.setSpaceBelow(message, 1);
		
		StyleContext sc = new StyleContext();
		timestamp = sc.addStyle("Timestamp",  message);
		timestamp.addAttribute(StyleConstants.Foreground, Color.LIGHT_GRAY);
[/PHP]

[PHP]
		addLogEntry("Loading values from file");
		Enumeration<Object> e = settings.keys();
		ArrayList<String> list = new ArrayList<String>(settings.size());
		while(e.hasMoreElements())
			list.add((String) e.nextElement());
		Collections.sort(list);
		for(String key : list)
			addLogEntry(String.format("%15s:%10s", key, settings.getProperty(key)));
		addLogEntry();
[/PHP]

[PHP]
	private void getTime() throws BadLocationException{
		Date date = new Date();
		SimpleDateFormat sdf = new SimpleDateFormat("HH:mm");
		log.insertString(log.getLength(), sdf.format(date)+" ", timestamp);
	}
	
	void addLogEntry(String entry){
		try {
			getTime();
			log.insertString(log.getLength(), entry, message);
		} catch (BadLocationException e) {
			e.printStackTrace();
		}
		addLogEntry();
	}
[/PHP]


This text won't display correctly in the JTextPane, I think it's because ' ' differ in size in the pane.
```

00:29 Loading values from file
00:29              Diagram:     120.0
00:29     color_Background:   -ff0100
00:29     color_Foreground:     -999a

```

---

### Post by kahumba on 2010-09-19
Or you could use HTML to format your code, google for it if needed.

---

### Post by SpinningAround on 2010-09-19
> **kahumba said:**
> Or you could use HTML to format your code, google for it if needed.

That might do it, if I change to Editorpane instead and use a table to represent the text data.

Thanks.

EDIT:
Might be easier to stick with textpane since it extends editorpane

---

### Post by myrtle1908 on 2010-09-19
> **SpinningAround said:**
> I think it's because ' ' differ in size in the pane.

So use a fixed width font eg. Courier.

---

### Post by Reiger on 2010-09-19
Do not use Courier, if you need a fixed width font in Java use: “Monospaced”.

The reason for this is that “Monospaced” is supposed to be guaranteed by the JVM to be mapped to an appropriate Fixed Width font, hence it is supposed to be alway available which you cannot assume for Courier.

---

### Post by SpinningAround on 2010-09-22
> **Reiger said:**
> Do not use Courier, if you need a fixed width font in Java use: “Monospaced”.

The reason for this is that “Monospaced” is supposed to be guaranteed by the JVM to be mapped to an appropriate Fixed Width font, hence it is supposed to be alway available which you cannot assume for Courier.

Thanks, that solved it :)

---

