---
title: "Question/problem with an LSL script."
date: 2009-07-07
forum: Programming Talk
---

### Post by unknownPoster on 2009-07-07
I know LSL is a fairly obscure language here, but I figured I would post it just to see if I can find a solution.

For those of you that don't know: [http://en.wikipedia.org/wiki/Linden_Scripting_Language](http://en.wikipedia.org/wiki/Linden_Scripting_Language)

I'm a developer for an educational island in Second Life.

I'm am currently working on a tour balloon for our facilities and I'm encountering a strange error.

The script:
```

// From the book:
//
// Introduction to Linden Scripting Language for Second Life
// by Jeff Heaton (Encog Dod in SL)
// ISBN: 1604390042
// Copyright 2007 by Heaton Research, Inc.

float SPEED = 1;
vector target;
list waypoints;
integer currentWaypoint;
string message;

// for loading notecard
string notecardName = "Configure Balloon";
key notecardQuery;
integer notecardIndex;

integer nextWayPoint()
{
    if( currentWaypoint>= llGetListLength(waypoints) )
    {
        llSay(0,"Ride over");
        return TRUE;
    }
    else
    {
        target = llList2Vector(waypoints,currentWaypoint);
        message = llList2String(waypoints,currentWaypoint+1);
        currentWaypoint+=2;
        return FALSE;
    }
    
}


default
{
    state_entry()
    {
        llSay(0,"Balloon loading waypoints...");
        notecardIndex = 0;
        notecardQuery = llGetNotecardLine(notecardName,notecardIndex++);    
    }
    
    dataserver(key query_id, string data) 
    {
        if ( notecardQuery == query_id) 
        {
            // this is a line of our notecard
            if (data == EOF) 
            {    
                llSay(0,"Data loaded, balloon ready...");
                state waiting;

            } else 
            {

                list temp = llCSV2List(data);
                
                vector vec = (vector)llList2String(temp,0);
                string str = llList2String(temp,1);
                waypoints+=[vec,str];
                notecardQuery = llGetNotecardLine(notecardName,notecardIndex++); 
            }
        }
    }
}

state running
{
    state_entry()
    {
        
        currentWaypoint = 0;
        llSitTarget(<0,-0.5,0.5>, llEuler2Rot(<0,0,-90>) );
        llSetText("",<255,0,0>,1.0);
        nextWayPoint();
        llSetTimerEvent(0.1);
    }
    
    timer()
    {
        vector pos = llGetPos();
        integer match = 0;
        
        if( llFabs(pos.x - target.x) < SPEED )
        {
            pos.x = target.x;
            match++;
        }
        else
        {
            if( pos.x > target.x )
                pos.x-=SPEED;
            else
                pos.x+=SPEED;
        }
        
        if( llFabs(pos.y - target.y) < SPEED )
        {
            pos.y = target.y;
            match++;
        }
        else
        {
            if( pos.y > target.y )
                pos.y-=SPEED;
            else
                pos.y+=SPEED;
        }
        
        if( llFabs(pos.z - target.z) < SPEED )
        {
            pos.z = target.z;
            match++;
        }
        else
        {
            if( pos.z > target.z )
                pos.z-=SPEED;
            else
                pos.z+=SPEED;
        }
        
        llSetPos(pos);
        
        if( match==3 )
        {
            string hold = message;
            if( nextWayPoint() )
                state waiting;
            llSay(0,hold);
        }
    }
    
}

state waiting
{
    state_entry()
    {
        llSay(0,"Balloon is waiting.");
    }
    
    link_message(integer sender_num, integer num, string str, key id)
    {
        if( str=="go" )
        {
            state countdown;
        }
    }
}

state countdown
{
    state_entry()
    {
        llSetTimerEvent(5);
        llSay(0,"Welcome to the balloon ride.  Balloon will launch in 5 seconds.  Please take your seats!");
    }
    
    timer()
    {
        state running;
    }
}

```My notecard is perfectly fine as far as I can tell.

The problem is that when the tour is complete, the balloon proceeds to move to southwestern corner of the island and it remains stuck there. It does not stop where it is supposed to. This error only started occurring with the recent update to the SL server/client.

Thanks.

---

### Post by Tony Flury on 2009-07-07
> **unknownPoster said:**
> I know LSL is a fairly obscure language here, but I figured I would post it just to see if I can find a solution.

For those of you that don't know: [http://en.wikipedia.org/wiki/Linden_Scripting_Language](http://en.wikipedia.org/wiki/Linden_Scripting_Language)

I'm a developer for an educational island in Second Life.

I'm am currently working on a tour balloon for our facilities and I'm encountering a strange error.

The script:
```

// From the book:
//
// Introduction to Linden Scripting Language for Second Life
// by Jeff Heaton (Encog Dod in SL)
// ISBN: 1604390042
// Copyright 2007 by Heaton Research, Inc.

float SPEED = 1;
vector target;
list waypoints;
integer currentWaypoint;
string message;

// for loading notecard
string notecardName = "Configure Balloon";
key notecardQuery;
integer notecardIndex;

integer nextWayPoint()
{
    if( currentWaypoint>= llGetListLength(waypoints) )
    {
        llSay(0,"Ride over");
        return TRUE;
    }
    else
    {
        target = llList2Vector(waypoints,currentWaypoint);
        message = llList2String(waypoints,currentWaypoint+1);
        currentWaypoint+=2;
        return FALSE;
    }
    
}


default
{
    state_entry()
    {
        llSay(0,"Balloon loading waypoints...");
        notecardIndex = 0;
        notecardQuery = llGetNotecardLine(notecardName,notecardIndex++);    
    }
    
    dataserver(key query_id, string data) 
    {
        if ( notecardQuery == query_id) 
        {
            // this is a line of our notecard
            if (data == EOF) 
            {    
                llSay(0,"Data loaded, balloon ready...");
                state waiting;

            } else 
            {

                list temp = llCSV2List(data);
                
                vector vec = (vector)llList2String(temp,0);
                string str = llList2String(temp,1);
                waypoints+=[vec,str];
                notecardQuery = llGetNotecardLine(notecardName,notecardIndex++); 
            }
        }
    }
}

state running
{
    state_entry()
    {
        
        currentWaypoint = 0;
        llSitTarget(<0,-0.5,0.5>, llEuler2Rot(<0,0,-90>) );
        llSetText("",<255,0,0>,1.0);
        nextWayPoint();
        llSetTimerEvent(0.1);
    }
    
    timer()
    {
        vector pos = llGetPos();
        integer match = 0;
        
        if( llFabs(pos.x - target.x) < SPEED )
        {
            pos.x = target.x;
            match++;
        }
        else
        {
            if( pos.x > target.x )
                pos.x-=SPEED;
            else
                pos.x+=SPEED;
        }
        
        if( llFabs(pos.y - target.y) < SPEED )
        {
            pos.y = target.y;
            match++;
        }
        else
        {http://jira.secondlife.com/browse/VWR-14561
            if( pos.y > target.y )
                pos.y-=SPEED;
            else
                pos.y+=SPEED;
        }
        
        if( llFabs(pos.z - target.z) < SPEED )
        {
            pos.z = target.z;
            match++;
        }
        else
        {
            if( pos.z > target.z )
                pos.z-=SPEED;
            else
                pos.z+=SPEED;
        }
        
        llSetPos(pos);
        
        if( match==3 )
        {
            string hold = message;
            if( nextWayPoint() )
                state waiting;
            llSay(0,hold);
        }
    }
    
}

state waiting
{
    state_entry()
    {
        llSay(0,"Balloon is waiting.");
    }
    
    link_message(integer sender_num, integer num, string str, key id)
    {
        if( str=="go" )
        {
            state countdown;
        }
    }
}

state countdown
{
    state_entry()
    {
        llSetTimerEvent(5);
        llSay(0,"Welcome to the balloon ride.  Balloon will launch in 5 seconds.  Please take your seats!");
    }
    
    timer()
    {
        state running;
    }
}

```My notecard is perfectly fine as far as I can tell.

The problem is that when the tour is complete, the balloon proceeds to move to southwestern corner of the island and it remains stuck there. It does not stop where it is supposed to. This error only started occurring with the recent update to the SL server/client.

Thanks.

have you tried to print out your list of way points use : 
```

llOwnerSay(llList2CSV(waypoints))

```

---

### Post by planetbrain on 2009-08-21
Don't know if this ever got solved, but I just tried the same script for a project I was working on abd had the same problem
Moving to 0,0,0 at the end.

Traked the problem down to blank lines at the end of the file containing the list of waypoints.

The last point MUST be the LAST line, anything after it even an empty lin is read by the script, and as it doesn't contain a valid vector is interpreted as <0,0,0>

---

