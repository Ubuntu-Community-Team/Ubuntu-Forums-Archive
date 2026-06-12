---
title: "Android XML Build Error"
date: 2011-01-01
forum: Programming Talk
---

### Post by muaaz007 on 2011-01-01
I am building a very simple Layout

<?xml version="1.0" encoding="utf-8"?>
<LinearLayout 
    xmlns:android="http://schemas.android.com/apk/res/android"
    android:orientation="vertical"
    android:layout_width="fill_parent"
    android:layout_height="fill_parent"
    >

<EditText 
    android:layout_width="fill_parent" 
    android:id="@+id/mytext" 
    android:layout_height="wrap_content"></EditText>


<Button 
    android:text="@string/button_text" 
    android:id="@+id/my_button" 
    android:layout_width="fill_parent" 
    android:layout_height="wrap_content"
    ></Button>
</LinearLayout>

<LinearLayout
    android:layout_width = "fill_parent"
    android:layout_height = "wrap_content"
    android:orientation = "horizontal"
    android:padding = "4dp"></LinearLayout>

On the Last Layout he is giving me an error:-
Multiple annotations found at this line:
    - The markup in the document following the root element must be well-
     formed.
    - error: Error parsing XML: junk after document element

I am very new at this so any help will be greatly appreciated.

---

### Post by Arndt on 2011-01-01
> **muaaz007 said:**
> I am building a very simple Layout

<?xml version="1.0" encoding="utf-8"?>
<LinearLayout 
    xmlns:android="http://schemas.android.com/apk/res/android"
    android:orientation="vertical"
    android:layout_width="fill_parent"
    android:layout_height="fill_parent"
    >

<EditText 
    android:layout_width="fill_parent" 
    android:id="@+id/mytext" 
    android:layout_height="wrap_content"></EditText>


<Button 
    android:text="@string/button_text" 
    android:id="@+id/my_button" 
    android:layout_width="fill_parent" 
    android:layout_height="wrap_content"
    ></Button>
</LinearLayout>

<LinearLayout
    android:layout_width = "fill_parent"
    android:layout_height = "wrap_content"
    android:orientation = "horizontal"
    android:padding = "4dp"></LinearLayout>

On the Last Layout he is giving me an error:-
Multiple annotations found at this line:
    - The markup in the document following the root element must be well-
     formed.
    - error: Error parsing XML: junk after document element

I am very new at this so any help will be greatly appreciated.

You have two LinearLayout elements as top elements. You can only have one top element in XML documents.

By the way, it may be a good idea to turn off smileys when you post XML code, since many character sequences got corrupted.

---

### Post by muaaz007 on 2011-01-01
Thank you and will turn off Smileys.

---

