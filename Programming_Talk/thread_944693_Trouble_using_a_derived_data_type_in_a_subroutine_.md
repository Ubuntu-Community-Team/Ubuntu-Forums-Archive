---
title: "Trouble using a derived data type in a subroutine - f90"
date: 2008-10-11
forum: Programming Talk
---

### Post by lordhaworth on 2008-10-11
The title says it all really. It could be something really simple im doing wrong, the snapshot of code that doesnt work is below

```

	TYPE GRID
		REAL	:: Temperature, Density
	END TYPE
	
	INTEGER	:: XMax = 100, YMax = 100
	TYPE(GRID),DIMENSION(XMax, YMax)	:: DataGrid

	INTERFACE
		SUBROUTINE Setup_Density_Distribution(InfoGrid)
			TYPE(GRID), DIMENSION(XMax, YMax), INTENT(INOUT)	:: InfoGrid
		END SUBROUTINE

		SUBROUTINE Setup_Temperature_Distribution(InfoGrid)
			TYPE(GRID), DIMENSION(XMax, YMax), INTENT(INOUT)	:: InfoGrid
		END SUBROUTINE
	END INTERFACE


```

So im basically defining a data type and wanting to pass an array of this data type to an external subroutine. However at the moment I get the following error message:

"Error: Derived type 'grid' at (1) is being used before it is defined"

I've tried re ordering the above code to no avail, I dont get it because I can get derived types to work, and I can get subroutines using an interface to work - just not together!

Any help or suggestions would be greatly appreciated!


Thanks very much all

Tom :)

---

### Post by WW on 2008-10-11
Wrap the type definition in a module, and use it before the declaration of the variables. E.g.
```

    module grid_type
        TYPE GRID
            REAL :: Temperature, Density
        END TYPE
    end module grid_type

    use grid_type	
    INTEGER :: XMax = 100, YMax = 100
    TYPE(GRID),DIMENSION(XMax, YMax) :: DataGrid

    INTERFACE
        SUBROUTINE Setup_Density_Distribution(InfoGrid)
            use grid_type
            TYPE(GRID), DIMENSION(XMax, YMax), INTENT(INOUT) :: InfoGrid
        END SUBROUTINE

        SUBROUTINE Setup_Temperature_Distribution(InfoGrid)
            use grid_type
            TYPE(GRID), DIMENSION(XMax, YMax), INTENT(INOUT) :: InfoGrid
        END SUBROUTINE
    END INTERFACE

```

---

### Post by lordhaworth on 2008-10-12
thats brilliant cheers, I never would have figured that out!

Thanks again

---

