---
title: "Modifying objects in an ArrayList [java]"
date: 2008-11-21
forum: Programming Talk
---

### Post by blackphiber on 2008-11-21
so lets say I have an arrayList
```
ArrayList<Team> teamArray=new ArrayList<Team>();
```

and I populate the array with a bunch of Team objects

```
for(int i=0; i<=numTeamsBox.getActive()+2; i++)
{
	Team aTeam=new Team();
	teamArray.add(aTeam);
}

```
and lets say the Team class is:

```
public class Team 
{
	int score;
	public Team()
	{
		score=0;
	}
	
	public void incrementScore()
	{
		score++;
	}
}

```
would it be possible for me to increment the score for each team object in the arrayList?

I guess I could just try, but figured I might as well just ask

teamArray.get(currentTeam).incrementScore();

probably a better solution. apologies if this is a stupid question...

---

### Post by cl333r on 2008-11-21
yeah, that would work as well. You modify the object, not the array it is in. so pretty much ok.

---

