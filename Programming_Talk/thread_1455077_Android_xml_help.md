---
title: "Android xml help"
date: 2010-04-15
forum: Programming Talk
---

### Post by matmatmat on 2010-04-15
Hi everyone, I'm trying to develop a todo app with the android sdk and eclipse, so far I've got a list view and I am able to create, edit and delete todo items. The problem I'm having is with the xml file that defines a row in the list view:
[PHP]
<?xml version="1.0" encoding="utf-8"?>

<TextView 
	android:id="@+id/text1" 
	android:layout_width="wrap_content" 
	android:layout_height="wrap_content" 
	xmlns:android="http://schemas.android.com/apk/res/android">
</TextView>

<TextView 
	android:id="@+id/text2" 
	android:layout_width="wrap_content" 
	android:layout_height="wrap_content" 
	xmlns:android="http://schemas.android.com/apk/res/android">
</TextView>
[/PHP]

Eclipse flags the second TextView with this:
```

Multiple annotations found at this line:
	- error: Error parsing XML: junk after document element
	- The markup in the document following the root element must be well-
	 formed.

```


It's used in this code:
[PHP]
	private void getData() {
		mCursor = mDb.fetchAllItems();
		startManagingCursor(mCursor);

		String[] cols = new String[]{ ListDbAdapter.DB_ITEM, ListDbAdapter.DB_PRI };
		int[] views   = new int[]{ R.id.text1, R.id.text2 };
		SimpleCursorAdapter row_cursor =
			new SimpleCursorAdapter(this, R.layout.list_row, mCursor, cols,
					views);
		setListAdapter(row_cursor);
	}


// --- db handle
    public Cursor fetchAllItems() {
        return listDb.query(DB_TABLE, new String[] {DB_ROWID, DB_ITEM, DB_PRI},
                null, null, null, null, null);
    }
[/PHP]

Can anybody tell me what I'm doing wrong?

---

### Post by Simon17 on 2010-04-16
I don't know anything about android, but that doesn't look like well-formed xml. Does your xml document have a root element?

I think you need to read the manual or some examples.

---

### Post by matmatmat on 2010-04-16
What do you mean by it not being well-formed? (The XML was generated in eclipse with the android plugin)

---

### Post by slavik on 2010-04-16
XML standard defines that there should be a root node, something along the lines of the following:
```

<?xml version="1.0" encoding="utf-8"?> 
<root>
<TextView  
    android:id="@+id/text1"  
    android:layout_width="wrap_content"  
    android:layout_height="wrap_content"  
    xmlns:android="http://schemas.android.com/apk/res/android"> 
</TextView> 

<TextView  
    android:id="@+id/text2"  
    android:layout_width="wrap_content"  
    android:layout_height="wrap_content"  
    xmlns:android="http://schemas.android.com/apk/res/android"> 
</TextView>
</root>

```

---

### Post by janfsd on 2010-04-17
You should be using something like LinearLayout or RelativeLayout as the root element. And put the line with xmlns:android in the root element only. Also, don't forget about having both android:layout_width and android:layout_height in the root.

---

### Post by Queue29 on 2010-04-17
A properly formatted android xml file will start off looking something like this:

```
<?xml version="1.0" encoding="utf-8"?>
<*AbsoluteLayout*
android:id="@+id/widget0"
android:layout_width="fill_parent"
android:layout_height="fill_parent"
android:background="#000000"
xmlns:android="http://schemas.android.com/apk/res/android"
> 

.. contents..

</*AbsoluteLayout*>

```

Where AbsoluteLayout is replaced with whatever kind of layout you want to use

---

### Post by janfsd on 2010-04-17
Don't use AbsoluteLayout, since it is deprecated.

---

