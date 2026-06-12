---
title: "grep: filtering the lexicographically smallest directory name?"
date: 2009-01-22
forum: Programming Talk
---

### Post by mangar on 2009-01-22
I'm trying to locate a specific device with in /Sys, according to the vendor Id.
Since the device got several subssystems, I get a list of files, while I need the lexicographically smallest directory name(since it's the first device in the pci-e tree).

How do I get the lexicographically smallest directory name? 

source:
```

#!/bin/sh
for i in `grep -li -m 1 $1 /sys/bus/pci/devices/*/vendor` ; do
	k=`dirname $i`
	if grep -qi $2 $k/device ; then j="$j $k" ; fi
done
echo $j
```


Is there a way to do it from a binary file?

---

### Post by mangar on 2009-01-22
```
/*
* scans the devices for the root complex of the 
*/
void getVIDSysLocation(char* returnString)
{
	FILE*	file;
	char	buffer[1024];
	long 	vendor_id 		= 0;
	struct 	dirent **namelist;
	int 	numberOfDirectories;

	//initializes the returnString to a large number
	strcpy(returnString,"FFFFFFFFFFFFFFFFFFFFFF");
		
	//get all the devices names:
	numberOfDirectories = scandir("/sys/bus/pci/devices/", &namelist, 0, alphasort);
	if (numberOfDirectories < 0) { perror("scandir");}
	
	//now go over all the devices, read "vendor", and compare to vendor id.
	for (int i = 0; i < numberOfDirectories; i++)
	{
		memset(buffer, 0, 1024);
		sprintf(buffer,"/sys/bus/pci/devices/%s/vendor",namelist[i]->d_name );

		file = fopen(buffer,"r");
	
		if (NULL != file) //find the first element of the tree
		{
			fscanf(file, "%0x", &vendor_id);
			if (VENDOR_ID == vendor_id)
			{
				if( strcmp( returnString, namelist[i]->d_name ) > 0 ) 
				{
				 	strcpy( returnString, namelist[i]->d_name ); 
				}
			}
		}
	}
	strcpy(buffer, returnString);
	sprintf(returnString,"/sys/bus/pci/devices/%s",buffer);
	
	while(numberOfDirectories--) { free(namelist[numberOfDirectories]); }
	free(namelist);
}
```

that's it, enjoy..

---

