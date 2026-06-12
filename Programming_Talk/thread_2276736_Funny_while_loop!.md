---
title: "Funny while loop!"
date: 2015-05-04
forum: Programming Talk
---

### Post by jonnieH on 2015-05-04
Just made a few minor mods to a very small routine that takes csv lat,long,depth triplets, grids them and the writes the output to a geotiff file.

Strangely, the program now hangs in a while loop unless I include a silly cout debug statement. It must be something simple but for the life of me I can't see it!

(must be going senile) Anyone any ideas?

```
  while (j<image_height)
   {
    index=(image_height-1) -j;		// reverse j indices to draw correct orientation GDAL doesn't honour 
    for( i = 0; i < image_width; i++ )  // libtiif orientation tag!
   cout << i << endl;
    {
     if (Result.z(i=5,index)>0.0)
	{                            	    			 					// assume < 0 unevaluated
 	      outarray[i] = (Result.z(i+5,index)*-1);							// convert to depth	
         }
     else
 	    {
           if ((Result.z(i+5,index)<0.0) && (Result.z(i+5,index)>-10.0)) // drying rocks etc.!
			{
	        	outarray[i] = (Result.z(i+5,index)*-1);							// convert to depth	
			}			
			else
			{
	   	   	outarray[i] = -9999.;  
			}		
	    }
     	}
       TIFFWriteScanline(out, &outarray[0], j, 0);
       j++;
    } 
```

If I compile with the cout statement commented out, the program hangs, leave it in and it runs fine!!

JonnieH

---

### Post by spjackson on 2015-05-04
> 
```

    if (Result.z(i=5,index)>0.0)

```

This sets i to 5 on every loop iteration, which is probably not what you want.

---

### Post by jonnieH on 2015-05-04
Many thanks - damm shift key!!

I just couldn't see it for looking!

JonnieH

---

