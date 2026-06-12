---
title: "VB.NET: Delegate to a property"
date: 2007-11-30
forum: Programming Talk
---

### Post by cwaldbieser on 2007-11-30
I have a function that processes data from the columns of an object.  I originally wrote the function with the assumption that the object in question would be an IDataReader, but I would like to be able to pass in a DataRow, too, since the only method being used is the **obj.Item("field_name")** property.

I thought that it should be possible to use a delegate to do this:
```

Private Delegate Function GetItemDelegate(ByVal name As String) As Object
...
Public Function ValidateRow(ByVal dr As IDataReader) As List(Of String)
    Dim GetItemD As GetItemDelegate = AddressOf dr.Item 'The compiler doesn't like this line
    Return ValidateRowImpl(GetItemD)
End Function

```

The compiler doesn't think the delegate signature and the IDataReader.Item signature match, though.  I think this is because it is a property rather than a Sub or Function, but I can't seem to figure out what the correct syntax would be.

Does anyone have any idea how I might accomplish something like this?

---

