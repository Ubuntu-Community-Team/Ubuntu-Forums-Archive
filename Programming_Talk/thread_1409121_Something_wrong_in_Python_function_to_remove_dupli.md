---
title: "Something wrong in Python function to remove duplicates"
date: 2010-02-17
forum: Programming Talk
---

### Post by Krijk on 2010-02-17
I'm trying to write  a function that fills a dictionary using the following rules and (example) data:

Rules:
* No duplicate values in field1
* No duplicates values in field2 and field3 (highest value in field4 has to be preserved)


Rec.no	field1,	field2,	field3,	field4
1.	abc, 	def123,	ghi123,	120   <-- new, insert in dictionary
2.	abc, 	def123,	ghi123,	120   <-- duplicate with 1. field4    same value. Do not insert in dictionary
3.	bcd,	def123, jkl125,	154   <-- new, insert in dictionary
4.	efg,	def123, jkl125,	175   <-- duplicate with 3 in field 2 and 3, but higher value in field4. Remove 3. from dict and replace with 4.
5. 	hij,	ghi345, jkl125,	175   <-- duplicate field3, but not in field4. New, insert in dict.


The resulting dictionary should be:
```
hij 	{'F2': ' ghi345', 'F3': ' jkl125', 'F4': 175}
abc 	{'F2': ' def123', 'F3': ' ghi123', 'F4': 120}
efg 	{'F2': ' def123', 'F3': ' jkl125', 'F4': 175}
```

This is wat I came up with up to now, but there is something wrong with it. The 'bcd' should have been removed. When I run it it says:
```
bcd 	{'F2': ' def123', 'F3': ' jkl125', 'F4': 154}
hij 	{'F2': ' ghi345', 'F3': ' jkl125', 'F4': 175}
abc 	{'F2': ' def123', 'F3': ' ghi123', 'F4': 120}
efg 	{'F2': ' def123', 'F3': ' jkl125', 'F4': 175}
```

Below is wat I brew (simplified). I'm staring so long at it now that I see too many if/else-statements :confused: and just don't see it anymore (and having changed it too many times.)

**Can somebody have a look at it and explain to me what goes wrong? (and maybe have an alternative for the nesting. Because I may need more comparisons). **

[PHP]def createResults(field1, field2, field3, field4):
        #check if field1 exists.
                if not results.has_key(field1):
                        
                        if results.has_key(field2):
                                #check if field2 already exists
                            
                                if results.has_key(field3):
                                    #check if field3 already exists
                                    #retrieve value field4
                                    existing_field4 = results[field2][F4]
                                    #retrieve value existing field1 in dict
                                    existing_field1 = results[field1]
                                    
                                    #perform highest value check
                                    if int(existing_field4) < int(field4):
                                        #remove existing record from dict.
                                        del results[existing_field1]
                                        values = {}
                                        values['F2'] = field2
                                        values['F3'] = field3
                                        values['F4'] = field4
                                        results[field1] = values
                                    else:
                                        pass
                                else:
                                    pass
                        else:
                            values = {}
                            values['F2'] = field2
                            values['F3'] = field3
                            values['F4'] = field4
                            results[field1] = values
                else:
                    pass
                
        


                         
for line in open("file.csv"):
        field1, field2, field3, field4 = line.split(',')
        createResults(field1, field2, field3, int(field4))

for i in results.keys():
        print i, '\t', results[i]
[/PHP]

contents file.csv

abc, def123, ghi123, 120
abc, def123, ghi123, 120
bcd, def123, jkl125, 154
efg, def123, jkl125, 175
hij, ghi345, jkl125, 175

---

