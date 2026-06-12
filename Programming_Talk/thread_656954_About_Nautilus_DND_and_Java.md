---
title: "About Nautilus DND and Java"
date: 2008-01-03
forum: Programming Talk
---

### Post by xlinuks on 2008-01-03
Hi there,
I'm creating a Java file manager for Ubuntu, things go well so far, by now I have a DND (= Drag And Drop) issue:
I know how to "import" (using DND) the files that I drag from Nautilus into the fm, so no problems here, but I also need to "export" files from my fm to Nautilus.
Here's a screenshot:
[http://xlinuks.googlepages.com/fm.png](http://xlinuks.googlepages.com/fm.png)
On the screenshot one can see that Nautilus "understands" the export as a "string" rather than a "file" so instead of copying the file he creates a text file and places in it the path of the file to be dragged.
How do I make it understand that I want it to "copy the file"?
Any link or idea would be highly appreciated..
A working example in other languages such as C/C++ would be appreciated as well (I guess I'll figure out how to do same in Java)..

If needed here's the class that suggests the type of data is being transferred:
```

class TransferableTH implements Transferable {
	private TableTH tableTH = null;
	private ArrayList<ExtFile> filesList = null;
	private StringBuilder sBuffer = null;
	private URIFlavor uriFlavor = null;
	
	public TransferableTH( TableTH tableTH ) {
		this.tableTH = tableTH;
		uriFlavor = new URIFlavor();
		filesList = new java.util.ArrayList<ExtFile>();
		ExtFile[] files = tableTH.getTable().getSelectedFiles();
		sBuffer = new StringBuilder();
		
		for( int i=files.length-1; i>=0; i-- ) {
			filesList.add( files[i] );
			sBuffer.append( "file://" + files[i].getPath() + "\r\n" );
		}
	}
	
	public Object getTransferData( DataFlavor flavor ) {
		
		if( flavor.equals( uriFlavor ) ) {
			return sBuffer.toString();
		} else if( flavor.equals( DataFlavor.javaFileListFlavor ) ) {
			return filesList;
		} else if( flavor.equals( DataFlavor.stringFlavor ) ) {
			return sBuffer.toString();
		}
		
		return null;
	}
	
	public DataFlavor[] getTransferDataFlavors() {
		DataFlavor[] dataFlavor = new DataFlavor[ 2 ];
		dataFlavor[0] = DataFlavor.javaFileListFlavor;
		//dataFlavor[1] = uriFlavor;
		dataFlavor[1] = DataFlavor.stringFlavor;
		return dataFlavor;
	}
	
	public boolean isDataFlavorSupported( DataFlavor flavor ) {
		return true;
	}
}

```

btw: I'm doing it in Java because I don't know C/C++

---

