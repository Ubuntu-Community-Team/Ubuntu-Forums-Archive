---
title: "Know enough to be dangerous how to deal with: cannot call member function without obj"
date: 2010-10-24
forum: Programming Talk
---

### Post by Jonas thomas on 2010-10-24
Ok... I think I'm missing something exceeding obvious..
So... here it is.
I'm trying to create this function checkForInvalidConstraint

I've declared it here in constraint.h

```

class Constraint : public HeeksObj{
public:
	ConstrainedObject* m_obj1;
	ConstrainedObject* m_obj2;

	EnumConstraintType m_type;
	EnumAbsoluteAngle m_angle;

	double m_length;

	Constraint();
	Constraint(const Constraint* obj);
	Constraint(EnumConstraintType,EnumAbsoluteAngle,ConstrainedObject* obj);
	Constraint(EnumConstraintType,double length,ConstrainedObject* obj);
	Constraint(EnumConstraintType,ConstrainedObject* obj);
	Constraint(EnumConstraintType,ConstrainedObject* obj1, ConstrainedObject* obj2);
	Constraint(EnumConstraintType,EnumAbsoluteAngle,double length,ConstrainedObject* obj1, ConstrainedObject* obj2);

	~Constraint(void);

	void ReloadPointers();
	bool IsTransient(){return true;}
	HeeksObj *MakeACopy(void)const;
	int GetType()const{return ConstraintType;}
	const wxChar* GetTypeString(void)const{return _("Constraint");}
	void Disconnect(std::list<HeeksObj*> parents);
	void WriteXML(TiXmlNode *root);
	static HeeksObj* ReadFromXMLElement(TiXmlElement* pElem);
	static void BeginSave();
	static void EndSave(TiXmlNode *root);
	bool IsDifferent(HeeksObj* other);

	bool operator==(const Constraint &other) const {
		return m_type == other.m_type && m_angle==other.m_angle && m_obj1 == other.m_obj1 && m_obj2 == other.m_obj2 && m_length == other.m_length;
	}

	const Constraint& operator=(const Constraint &b);

	void glCommands(HeeksColor color, gp_Ax1 mid_point);
	void render_text(const wxChar* str);
	//JT This my attempt to isolate some constraint bugs.
#ifdef CHECK_FOR_INVALID_CONSTRAINT
    //bool checkForInvalidConstraint(char* type,EnumConstraintType etype,char* angle,EnumAbsoluteAngle eangle,double length,int obj1_id,int obj2_id,int obj1_type);
    **bool checkForInvalidConstraint()**;
#endif

};

```

I attempt to implement this function as such.
```
#ifdef CHECK_FOR_INVALID_CONSTRAINT
//bool Constraint::checkForInvalidConstraint( char* type, EnumConstraintType etype,char* angle,EnumAbsoluteAngle eangle,double length,int obj1_id,int obj2_id,int obj1_type)
[B]bool Constraint::checkForInvalidConstraint( )
{
    wxMessageBox(_("Hello world"));
    return false;//false says all is well
}
#endif[/B]
```

I try to use this function within another member function here..


```

HeeksObj* Constraint::ReadFromXMLElement(TiXmlElement* pElem)
{
	const char* type=0;
	EnumConstraintType etype=(EnumConstraintType)0;
	const char* angle=0;
	EnumAbsoluteAngle eangle=(EnumAbsoluteAngle)0;
	double length=0;
	int obj1_id=0;
	int obj2_id=0;
	int obj1_type=0;
	int obj2_type=0;
	ConstrainedObject* obj1=0;
	ConstrainedObject* obj2=0;
	// get the attributes
	for(TiXmlAttribute* a = pElem->FirstAttribute(); a; a = a->Next())
	{
		std::string name(a->Name());
		if(name == "type"){type = a->Value();}
		else if(name == "angle"){angle = a->Value();}
		else if(name == "length"){length = a->DoubleValue();}
		else if(name == "obj1_id"){obj1_id = a->IntValue();}
		else if(name == "obj1_type"){obj1_type = a->IntValue();}
		else if(name == "obj2_id"){obj2_id = a->IntValue();}
		else if(name == "obj2_type"){obj2_type = a->IntValue();}
	}

	//Ugh, we need to convert the strings back into types
	for(unsigned i=0; i < sizeof(ConstraintTypes); i++)
	{
		if(strcmp(ConstraintTypes[i].c_str(),type)==0)
		{
			etype = (EnumConstraintType)i;
			break;
		}
	}

	for(unsigned i=0; i < sizeof(AbsoluteAngle); i++)
	{
		if(strcmp(AbsoluteAngle[i].c_str(),angle)==0)
		{
			eangle = (EnumAbsoluteAngle)i;
			break;
		}
	}


	//JT
	//Ok.. There is a problem here.. Further up stream there a conditions where the xml has been written out for obj1_id, obj2_id != 0 for objects that don't exist
	//This is a huge pain, since the error is being introduced on the file save, and doesn't show up, until you load the file.
	// Sometimes you get a segmentation fault right at load... Or when you're really lucky it shows up when solvesketch kicks in and you have no clue whats going on.
    // At this point,until these critters get irridicated CheckforValidConstraint basically tries to see if the constraint makes sense
    // I hope to install this at both ends when constraints are being written out or read in my attempt to identify, isolate and irradicate these most annoying
    // critters

#ifdef CHECK_FOR_INVALID_CONSTRAINT
    bool blockConstraint =false;
    //blockConstraint = checkForInvalidConstraint(type,etype,angle,eangle,length,obj1_id,obj2_id,obj1_type);
    **blockConstraint = checkForInvalidConstraint();**
	if (blockConstraint)
	{
      wxMessageBox(_("A bad constraint from the XML file is being blocked from entering Heekscad"));
      return NULL;
    }
#endif

	//Get real pointers to the objects
	obj1 = (ConstrainedObject*)wxGetApp().GetIDObject(obj1_type,obj1_id);
	obj2 = (ConstrainedObject*)wxGetApp().GetIDObject(obj2_type,obj2_id);

	Constraint *c = new Constraint(etype,eangle,length,obj1,obj2);
```

I get this message when I try to compile:
/home/jonas/HeeksCAD/src/Constraint.cpp|355|error: cannot call member function ‘bool Constraint::checkForInvalidConstraint()’ without object|

Ok... this sort of makes sense to me... I thought maybe I need to change the line from:
**blockConstraint = checkForInvalidConstraint();**
to:
**blockConstraint = this.checkForInvalidConstraint();**

When I do that I get this.
/home/jonas/HeeksCAD/src/Constraint.cpp|355|error: ‘this’ is unavailable for static member functions|

:confused:

Like I said... I know I'm missing something really fundamental here...

---

### Post by GeneralZod on 2010-10-24
ReadFromXMLElement is a static method, and so is not associated with an object (and so, has no "this" pointer, implicit or otherwise).

checkForInvalidConstraint() is non-static and so cannot be called from a static method without an object e.g. someConstraintObject.checkForInvalidConstraint() or someConstraintObjectPtr->checkForInvalidConstraint().

---

### Post by SledgeHammer_999 on 2010-10-24
I think it has something to do with **ReadFromXMLElement** being static. Keep in mind that static member methods can be called without needing to create an instance of the class. And I think they cannot use member methods/attributes too. I could be wrong though for the last statement.

EDIT: **GeneralZod** beat me to it.

---

### Post by Jonas thomas on 2010-10-24
> **GeneralZod said:**
> ReadFromXMLElement is a static method, and so is not associated with an object (and so, has no "this" pointer, implicit or otherwise).

checkForInvalidConstraint() is non-static and so cannot be called from a static method without an object e.g. someConstraintObject.checkForInvalidConstraint() or someConstraintObjectPtr->checkForInvalidConstraint().


Thanks that makes sense...
I think I need my function needs to mimic how GetIDObject was implemented and then all should be well... If not... well, I'll be back...

Thanks..

---

