---
title: "Flex - AdvancedDataGrid"
date: 2009-11-08
forum: Programming Talk
---

### Post by nebu on 2009-11-08
```
<mx:AdvancedDataGrid id="data" designViewDataType="flat" horizontalCenter="-10" verticalCenter="-12" height="432" width="720" selectionMode="singleRow" dataProvider="{sponsors}">
						<mx:columns>
							<mx:AdvancedDataGridColumn headerText="Company Name" dataField="company"/>
							<mx:AdvancedDataGridColumn headerText="Place" dataField="place"/>
							<mx:AdvancedDataGridColumn headerText="Contact Person" dataField="contact"/>
							<mx:AdvancedDataGridColumn headerText="Mobile" dataField="mobile"/>
							<mx:AdvancedDataGridColumn headerText="Landline" dataField="landline"/>
							<mx:AdvancedDataGridColumn headerText="E-Mail" dataField="email"/>
							<mx:AdvancedDataGridColumn headerText="Status" dataField="status"/>
						</mx:columns>
					</mx:AdvancedDataGrid>
```

what is wrog with this code??

my compiler says--
> 
Could not resolve <mx:AdvancedDataGrid> to a component implementation


---

### Post by delfick on 2009-11-08
what version of flex are you using ??

---

### Post by nebu on 2009-11-08
flex 3

---

### Post by delfick on 2009-11-08
hmmm, quick google of your error message landed this

[http://forums.adobe.com/thread/482982](http://forums.adobe.com/thread/482982)

it seems it's not included with the free sdk.....

---

