---
title: "Python: remove non-unique entries"
date: 2009-09-09
forum: Programming Talk
---

### Post by j.bell730 on 2009-09-09
I've developed a Python script that will fetch me all my songs from my Last.fm profile. It works great, but the output contains some duplicates (stupid Last.fm radio, playing duplicates :P):
```
10 Years - Wasteland
3 Doors Down - Away from the Sun
3 Doors Down - Here Without You
+44 - 155
+44 - Lycanthrope
+44 - When Your Heart Stops Beating
Acceptance - Different
Acceptance - Permanent
Acceptance - So Contagious
Acceptance - Take Cover
Adema - Giving In
Adema - The Way You Like It
Against Me! - Thrash Unreal
Alien Ant Farm - Smooth Criminal
Alien Ant Farm - Wish
Alkaline Trio - This Could Be Love
Alkaline Trio - We've Had Enough
All Time Low - Coffee Shop Soundtrack
All Time Low - Dear Maria
All Time Low - Dear Maria, Count Me In
All Time Low - Jasey Rae
All Time Low - Jasey Rae (Acoustic)
All Time Low - Walls
Amber Pacific - Always You (Good Times)
Amber Pacific - Everything We Were Has Become What We Are
Amber Pacific - Fall Back Into My Life
Amber Pacific - Falling Away
Amber Pacific - Gone So Young
Amber Pacific - Postcards
Amber Pacific - Summer (In B)
American Hi-Fi - Flavor of the Weak
American Hi-Fi - The Art of Losing
Anberlin - Feel Good Drag
Armor for Sleep - Car Underwater
Ashley Parker Angel - Let U Go
Atreyu - Ex's and Oh's
Atreyu - Falling Down
Atreyu - Lose It
Audioslave - Doesn't Remind Me
Audioslave - I Am the Highway
Audioslave - Like a Stone
Audioslave - Show Me How to Live
Augustana - Boston
Augustana - Fire
Augustana - Stars & Boulevards
Augustana - Stars and Boulevards
Augustana - Sweet and Low
Augustana - Wasteland
Avril Lavigne - Complicated
Avril Lavigne - Everything Back But You (Explicit Version)
Avril Lavigne - Girlfriend
Avril Lavigne - Girlfriend (Junkie XL Mix)
Avril Lavigne - Hot
Avril Lavigne - I'm With You
Avril Lavigne - One of Those Girls
Avril Lavigne - Tomorrow
Barenaked Ladies - One Week
Barenaked Ladies - Pinch Me
Better Than Ezra - Desperately Wanting
blink-182 - Adam's Song
blink-182 - Aliens Exist
blink-182 - All Of This
blink-182 - All The Small Things
blink-182 - Always
blink-182 - Another Girl Another Planet
blink-182 - Anthem Part Two [Live In Chicago] [Bonus Track]
blink-182 - Asthenia
blink-182 - Bonus Track 15
blink-182 - Bonus Track 2
blink-182 - Bonus Track 3
blink-182 - Bonus Track 6
blink-182 - Dammit
blink-182 - Dick Lips
blink-182 - Down
blink-182 - Dumpweed
blink-182 - Easy Target
blink-182 - Feeling This
blink-182 - Feeling This (Album Version (Explicit))
blink-182 - Fentoozler
blink-182 - First Date
blink-182 - Go
blink-182 - GO  Version (Explicit))
blink-182 - Here's Your Letter
blink-182 - Here's Your Letter  Version (Explicit))
blink-182 - I Miss You
blink-182 - I'm Lost Without You
blink-182 - Man Overboard
blink-182 - M+M's
blink-182 - Mutt
blink-182 - Not Now [bonus track]
blink-182 - Obvious
blink-182 - Obvious (Album Version (Edited))
blink-182 - Online Songs
blink-182 - Reebok Commercial
blink-182 - Rock Show
blink-182 - Shut Up
blink-182 - Stay Together For The Kids
blink-182 - Stockholm Syndrome
blink-182 - Stockholm Syndrome (Album Version)
blink-182 - The Fallen Interlude
blink-182 - The Longest Line
blink-182 - The Party Song
blink-182 - The Rock Show
blink-182 - TV
blink-182 - Violence
blink-182 - Wendy Clear
blink-182 - What's My Age Again?
blink-182 - What Went Wrong
Bliss 66 - Sooner or Later
Bowling for Soup - 1985
Bowling for Soup - Almost
Bowling for Soup - Girl All the Bad Guys Want
Bowling for Soup - Punk Rock 101
Box Car Racer - I Feel So
Box Car Racer - Letters To God
Box Car Racer - There Is
Boys Like Girls - Five Minutes to Midnight
Boys Like Girls - Heels Over Head
Boys Like Girls - Heels Over Head (Tom Lord-Alge Mix)
Boys Like Girls - Hero/Heroine
Boys Like Girls - Love Drunk
Boys Like Girls - On Top of the World
Boys Like Girls - The Great Escape
Boys Like Girls - Thunder
Boys Like Girls - Thunder (Radio Mix)
Boys Like Girls - Up Against the Wall
Brand New - I Will Play My Game Beneath the Spin Light
Brand New - Seventy Times 7
Brand New - Seventy Times Seven
Brand New - Sic Transit Gloria...Glory Fades
Breaking Benjamin - Breath
Breaking Benjamin - Polyamorous
Breaking Benjamin - Sooner Or Later
Breaking Benjamin - The Diary of Jane
Breathe Carolina - See You Again
Burn Halo - Dirty Little Girl
Burn Halo - Here With Me
Burn Halo - Saloon Song
Burn Halo - Save Me
Caramell - Caramelldansen (speedycake remix)
Carolina Liar - Show Me What I'm Looking For
Carrie Underwood - All-American Girl
Cascada - Everytime We Touch
Cascada - Everytime We Touch (Radio Mix)
Chairlift - Bruises
Chevelle - Jars
Chevelle - Send the Pain Below
Chevelle - The Red
Coldplay - Clocks
Coldplay - Viva La Vida
Collective Soul - Shine
Collective Soul - The World I Know
Collective Soul - Tremble for My Beloved
Creed - Higher
Creed - My Own Prison
Creed - My Sacrifice
Creed - One Last Breath
Crossfade - Cold
Crossfade - Colors
Crossfade - So Far Away
Daft Punk - Around the World
Daft Punk - Da Funk
Daft Punk - Harder, Better, Faster, Stronger
Daft Punk - One More Time
Daft Punk - Revolution 909
Daft Punk - Robot Rock
Daft Punk - Technologic
Darude - Sandstorm
Dashboard Confessional - Again I Go Unnoticed
Dashboard Confessional - Don't Wait
Dashboard Confessional - Hands Down
Dashboard Confessional - Stolen
Dashboard Confessional - Vindicated
Daughtry - All These Lives
Daughtry - Crashed
Daughtry - Crashed (Acoustic)
Daughtry - Feels Like Tonight
Daughtry - Gone
Daughtry - Home
Daughtry - Home (Acoustic)
Daughtry - It's Not Over
Daughtry - No Surprise
Daughtry - Over You
Daughtry - Used To
Daughtry - What About Now
Daughtry - What About Now (Acoustic)
Daughtry - What I Want (feat. Slash)
David Cook - Come Back to Me
David Cook - Light On
David Cook - The Time of My Life
Dead Poetic - New Medicines
Dead Poetic - The Dream Club Murders
Deep Blue Something - Breakfast at Tiffany's
Def Leppard - Bringin' on the Heartbreak
Def Leppard - Foolin'
Def Leppard - Hysteria
Def Leppard - Love Bites
Def Leppard - Photograph
Def Leppard - Pour Some Sugar on Me
Digital Excitation - Sunburst
Digital Excitation - Sunburst (Cubic 22 Remix)
Disturbed - Believe
Disturbed - Land of Confusion
Disturbed - Liberate
Disturbed - Prayer
Disturbed - Stupify
Disturbed - The Night
Disturbed - Violence Fetish
Disturbed - Voices
DJ Jürgen Ft. Alice Deejay - Better off alone
Dj Mangoo - Eurodancer
Driving East - Blue Eyes
Driving East - Get Back
Echinasia - Sightline
Evanescence - Bring Me To Life
Evanescence - Call Me When You're Sober
Evanescence - Everybody's Fool
Evanescence - Going Under
Evanescence - Lies
Evanescence - Lithium
Evanescence - Missing
Evanescence - My Immortal (band version)
Evanescence - My Last Breath
Evanescence - Sweet Sacrifice
Evanescence - Whisper
Eve 6 - Here's to the Night
Eve 6 - Inside Out
Everclear - AM Radio
Everlast - What It's Like
Faber Drive - Second Chance
Faber Drive - Tongue Tied
Feist - 1234
Finch - Letters to You
Finch - Letters to You (album version)
Finch - Stay With Me
Finch - What It Is to Burn
Flaw - Get Up Again
Flaw - Get Up Again (Album Version)
Flaw - My Letter
Flaw - Only The Strong [Piano Acoustic]
Foo Fighters - Best of You
Foo Fighters - My Hero
Foo Fighters - The Pretender
Foo Fighters - Times Like These
Forever the Sickest Kids - Whoa Oh! (Me Vs Everyone)
Forever the Sickest Kids - Whoa Oh! (Me Vs. Everyone)
Fountains of Wayne - Stacy's Mom
Framing Hanley - Lollipop
Fuel - Bad Day
Fuel - Falls on Me
Fuel - Hemorrhage (In My Hands)
Fuel - Shimmer
Fuel - Shimmer (Single Version)
Gin Blossoms - Follow You Down
Gin Blossoms - Found Out About You
Gin Blossoms - Hey Jealousy
Guns N' Roses - Live and Let Die
Guns N' Roses - November Rain
Guns N' Roses - Paradise City
Guns N' Roses - Sweet Child o' Mine
Guns N' Roses - Welcome to the Jungle
Halifax - nightmare
Halifax - Sydney
Hey Monday - Run, Don't Walk
Hidden in Plain View - Bleed for You
Hinder - Better Than Me
Hinder - Lips of an Angel
Hinder - Without You
Hit the Lights - Bodybag
Hit the Lights - Body Bag (Album Version)
Hoobastank - Crawling in the Dark
Hoobastank - Out of Control
Hoobastank - Running Away
Hoobastank - The Reason
Incubus - Anna Molly
Incubus - Drive
Incubus - Drive (Live "Bootleg" Version - Stockholm, Sweden)
Incubus - Wish You Were Here
Incubus - Wish You Were Here (Live "Bootleg" Version - Stockholm, Sweden)
Jack's Mannequin - Dark Blue
Jet - Are You Gonna Be My Girl
Jet - Look What You've Done
Jimmy Eat World - A Sunday
Jimmy Eat World - Big Casino
Jimmy Eat World - Kill
Jimmy Eat World - Sweetness
Journey - Any Way You Want It
Journey - Don't Stop Believin'
Journey - Don't Stop Believin' (Live Version)
Journey - Lights
Keane - Somewhere Only We Know
Kids in the Way - Apparitions of Melody
Kids in the Way - Better Times
Kids in the Way - Fiction
Kids in the Way - Your Demon
Killswitch Engage - Holy Diver
Killswitch Engage - My Curse
Killswitch Engage - Numbered Days (Album Version)
Killswitch Engage - The Arms of Sorrow
Killswitch Engage - The End of Heartache
Kings of Leon - Red Morning Light
Kings of Leon - Use Somebody
Linkin Park - Faint
Linkin Park - Leave Out All the Rest
Linkin Park - Numb
Linkin Park - Papercut
Linkin Park - Somewhere I Belong
Linkin Park - What I've Done
Lit - Four
Lit - Happy in the Meantime
Lit - Lipstick and Bruises
Lit - Miserable
Lit - My Own Worst Enemy
Lit - Over My Head
Lit - Pictures of You
Lit - Slip
Lit - Something to Someone
Lit - Times Like This
Lit - Zip-Lock
Lostprophets - Always, all ways
Lostprophets - Always All Ways (Apologies, Glances and Messed Up Chances)
Lostprophets - Can't Catch Tomorrow (Good Shoes Won't Save You This Time)
Lostprophets - Can't Stop, Gotta Date with Hate
Lostprophets - Last Train Home
Lostprophets - Rooftops (A Liberation Broadcast)
LoveSick Radio - Boys Don't Matter
Madina Lake - Here I Stand
Madina Lake - Here I Stand (LP Version)
Maroon 5 - This Love
Matchbook Romance - Monsters
Matchbook Romance - My Eyes Burn
Matchbook Romance - Promise
Mayday Parade - Jamie All Over
Mest - I Melt With You (Mest)
Mest - Olqliuhqui
Mest - Rooftops
Mest - Rooftops (Album Version)
Metallica - Enter Sandman
Metallica - One
Metallica - The Unforgiven
Mudvayne - Do What You Do
Mudvayne - Happy?
Mudvayne - Happy (Demo)
Muse - New Born
Muse - Time Is Running Out
My Chemical Romance - Helena
My Chemical Romance - I'm Not Okay (I Promise)
My Chemical Romance - I'm Not OK (I Promise)
My Chemical Romance - Teenagers
My Chemical Romance - Welcome to the Black Parade
NEEDTOBREATHE - We Could Run Away
Oasis - Champagne Supernova
Oasis - Champagne Supernova (Live at Wembley Stadium, 2000)
Oasis - Cigarettes & Alcohol
Oasis - Don't Go Away
Oasis - Some Might Say
Oasis - Wonderwall
Oasis - Wonderwall (Live at Wembley Stadium, 2000)
OK Go - Get Over It
OneRepublic - All We Are
OneRepublic - Apologize
OneRepublic - Someone To Save You
OneRepublic - Stop And Stare
Our Lady Peace - Life
Our Lady Peace - Somewhere Out There
Our Lady Peace - Somewhere Out There (Calgary/Edmonton Live Show Version)
Papa Roach - Last Resort
Papa Roach - Lifeline
Paramore - Misery Business
Paramore - That's What You Get
Pearl Jam - Wishlist
Pogo - Expialidocious
Pop Evil - 100 In A 55
Pop Evil - 100 In a 55 (Album Version)
Pop Evil - Hero
Pop Evil - Somebody Like You
Pop Evil - Somebody Like You (Album Version)
Quietdrive - I Lie Awake
Quietdrive - Rise From The Ashes
Quietdrive - Rise From The Ashes (New Album Version)
Red - Breathe into me
Red - Breathe Into Me (Live)
Red Hot Chili Peppers - By the Way
Red Hot Chili Peppers - Californication
Red Hot Chili Peppers - Dani California
Red Hot Chili Peppers - Especially in Michigan
Red Hot Chili Peppers - Otherside
Red Hot Chili Peppers - Scar Tissue
Red Hot Chili Peppers - Under the Bridge
Rise Against - Give It All
Rise Against - Give It All (Album Version)
Rise Against - Injection
Rise Against - Prayer of the Refugee
Rise Against - Ready to Fall
Rise Against - Re education through labour
SafetySuit - Stay
Saliva - Rest in Pieces
Saosin - It's Far Better To Learn
Saosin - Seven Years
Saosin - You're Not Alone
Saving Abel - 18 Days
Saving Abel - Drowning (Face Down)
Scorpions - Big City Nights
Scorpions - No One Like You
Scorpions - Rock You Like a Hurricane
Scorpions - Send Me an Angel
Scorpions - Still Loving You
Scorpions - The Zoo
Secondhand Serenade - Fall For You
Secondhand Serenade - Why
Seether - Broken
Seether - Broken (feat. Amy Lee)
Seether - Careless Whisper
Seether - Fine Again
Seether - Remedy
Seether - Rise Above This
Seether - Truth
Senses Fail - Ali For Cody
Senses Fail - Angela Baker and My Obsession
Senses Fail - Angela Baker and My Obsession With Fire
Senses Fail - Bite to Break Skin
Senses Fail - Buried a Lie
Senses Fail - Calling All Cars
Senses Fail - Can't Be Saved
Senses Fail - Choke on This
Senses Fail - Family Tradition
Senses Fail - Four Years
Senses Fail - Hair of the Dog
Senses Fail - Irony Of Dying On Your Birthda
Senses Fail - Irony of Dying on Your Birthday
Senses Fail - Lady in a Blue Dress
Senses Fail - Let It Enfold You
Senses Fail - Life Is Not a Waiting Room
Senses Fail - Martini Kiss
Senses Fail - NJ Falls Into the Atlantic
Senses Fail - Rum Is for Drinking Not for Burning
Senses Fail - Rum Is for Drinking, Not for Burning
Senses Fail - Slow Dance
Senses Fail - The Irony of Dying on Your Birthday
Senses Fail - The Priest And The Matador
Senses Fail - Tie Her Down
Senses Fail - You're Cute When You Scream
Shinedown - 45 (Album Version)
Shinedown - I Dare You
Shinedown - Second Chance
Sick Puppies - All The Same
Sick Puppies - ******* Father
Sick Puppies - Too Many Words
Silverstein - Apologize
Silverstein - My Heroine
Silverstein - Smile in Your Sleep
Simple Plan - Crazy
Simple Plan - Everytime
Simple Plan - I'm Just a Kid
Simple Plan - One
Simple Plan - Perfect
Simple Plan - Promise
Simple Plan - Shut Up
Simple Plan - Untitled
Simple Plan - Welcome to My Life
Simple Plan - What If
Sing It Loud - Come Around (Acoustic)
Skid Row - 18 And Life
Skid Row - I Remember You
Skid Row - I Remember You  (LP Version)
Slipknot - Dead Memories
Slipknot - Duality
Slipknot - Vermilion, Pt. 2
Snow Patrol - Spitting Games
Something Corporate - As You Sleep
Something Corporate - Hurricane
Something Corporate - If You C Jordan
Something Corporate - I Want to Save You
Something Corporate - I Woke Up in a Car
Something Corporate - Konstantine
Something Corporate - Punk Rock Princess
Something Corporate - The Astronaut
Soul Asylum - Runaway Train
Soul Asylum - Runaway Train (live)
SR-71 - Right Now
Staind - Epiphany
Staind - Epiphany (LP Version)
Staind - For You
Staind - It's Been Awhile
Staind - Outside
Staind - Price to Play
Staind - So Far Away
State of Shock - Best I Ever Had
Stone Sour - Bother
Story of the Year - Anthem of Our Dying Day
Story of the Year - In the Shadows
Story of the Year - Razorblades
Story of the Year - Sidewalks
Story of the Year - Until the Day I Die
Sublime - Santeria
Sublime - What I Got
Sugarcult - Bouncing Off the Walls
Sugarcult - Dead Living
Sugarcult - Do It Alone
Sugarcult - Explode
Sugarcult - Hate Every Beautiful Day
Sugarcult - Head Up
Sugarcult - Memory
Sugarcult - Out Of Phase
Sugarcult - She's the Blade
Sugarcult - The Investigation
Sum 41 - Fat Lip
Sum 41 - Fat Lip  Version (Edited))
Sum 41 - In Too Deep
Sum 41 - No Reason
Sum 41 - Pieces
Switchfoot - Dare You to Move
Switchfoot - Dare You To Move (alternative version)
Switchfoot - Dare You To Move (Live)
System of a Down - Aerials
System of a Down - Chic 'n' Stu
System of a Down - Chop Suey!
System of a Down - Prison Song
System of a Down - Psycho
System of a Down - Science
System of a Down - Shimmy
System of a Down - Toxicity
System of a Down - Toxicity (Live Version)
Taking Back Sunday - Cute Without the 'E' (Cut From the Team)
Taking Back Sunday - Liar (It Takes One To Know One)
Taking Back Sunday - Number Five With a Bullet
Taylor Swift - Fearless
Taylor Swift - Love Story
Taylor Swift - Teardrops on My Guitar
Taylor Swift - White Horse
Taylor Swift - You Belong With Me
Tenacious D - Tribute
The All-American Rejects - Dirty Little Secret
The All-American Rejects - Gives You Hell
The All-American Rejects - It Ends Tonight
The All-American Rejects - I Wanna
The All-American Rejects - Move Along
The All-American Rejects - My Paper Heart
The All-American Rejects - The Wind Blows
The All-American Rejects - Top of the World
The Ataris - The Boys of Summer
The Ataris - The Hero Dies in This One
The Ataris - The Hero Dies in This One (Acoustic Version)
The Calling - Wherever You Will Go
The Cars - Drive
The Cars - Drive (LP Version)
The Cars - Good Times Roll
The Cars - Just What I Needed
The Cars - Let's Go
The Cars - Magic
The Cars - Moving in Stereo
The Cars - My Best Friend's Girl
The Cars - You Might Think
The Cars - You Might Think  (LP Version)
The Cars - You're All I've Got Tonight
The Classic Crime - The Coldest Heart
The Classic Crime - The Fight
The Click Five - Just the Girl
The Click Five - Just The Girl (Album Version)
The Click Five - Time Machine
The Click Five - Time Machine (Album Version)
The Darkness - I Believe in a Thing Called Love
The Fratellis - Flathead
The Fray - All at Once
The Fray - How to Save a Life
The Fray - How To Save A Life (Live At The Electric Factory)
The Fray - Look After You
The Fray - Never Say Never
The Fray - Over My Head (Cable Car)
The Fray - Over My Head (Cable Car) (Acoustic)
The Fray - Over My Head (Cable Car) (Acoustic Version)
The Fray - She Is
The Fray - You Found Me
The Killers - Somebody Told Me
The Lonely Island - I'm on a Boat (feat. T-Pain)
The Offspring - Kids Aren't Alright
The Offspring - Kristy, Are You Doing Okay?
The Offspring - The Kids Aren't Alright
The Section Quartet - Heartbreaker
The Section Quartet - Such Great Heights
The Section Quartet - Time Is Running Out
The Spill Canvas - All Hail the Heartbreaker
The Spill Canvas - All Over You
The Spill Canvas - Appreciation and the Bomb
The Spill Canvas - Battles
The Spill Canvas - Homesick
The Spill Canvas - Hush Hush
The Spill Canvas - Low Fidelity
The Spill Canvas - Lullaby
The Spill Canvas - Polygraph, Right Now
The Spill Canvas - Reckless Abandonment
The Spill Canvas - Saved
The Spill Canvas - Staplegunned
The Spill Canvas - Still Walking After You
The Starting Line - Best of Me
The String Quartet - A Box Full of Sharp Objects
The String Quartet - All That I've Got
The String Quartet - Bite To Break Skin
The String Quartet - Buddy Holly
The String Quartet - Buried A Lie
The String Quartet - Clocks
The String Quartet - Cute Without The ‘E’ (Cut From The Team)
The String Quartet - Go with the Flow
The String Quartet - Helena
The String Quartet - Hell Song
The String Quartet - I Caught Fire
The String Quartet - I'm Not Okay (I Promise)
The String Quartet - In The End
The String Quartet - Lady In A Blue Dress
The String Quartet - Misery Business
The String Quartet - Mr. Brightside
The String Quartet - My Immortal
The String Quartet - NJ Falls Into The Atlantic
The String Quartet - Number Five With A Bullet
The String Quartet - Ocean Avenue
The String Quartet - Reinventing Your Exit
The String Quartet - scar tissue
The String Quartet - Science
The String Quartet - Somewhere I Belong
The String Quartet - still waiting
The String Quartet - Take It Away
The String Quartet - The Taste of Ink
The String Quartet - Tie Her Down
The String Quartet - Time Is Running Out
The String Quartet - Times Like These
The Used - Buried Myself Alive
The Used - Pretty Handsome Awkward
The Used - Sick Hearts
The Used - Sound Effects and Overdramatics
The Used - Sun Comes Up
The Used - The Taste of Ink
Third Eye Blind - How's It Going to Be
Third Eye Blind - Jumper
Third Eye Blind - Never Let You Go
Third Eye Blind - Semi-Charmed Life
Three Days Grace - Animal I Have Become
Three Days Grace - Animal I Have Become (Stripped Acoustic Version)
Three Days Grace - Never Too Late
Three Days Grace - Never Too Late (Main Version)
Tinted Windows - Dead Serious
Tinted Windows - Kind of a Girl
Train - Drops of Jupiter
Train - Drops of Jupiter (live)
Train - Meet Virginia
TRUSTcompany - Downfall
TRUSTcompany - Stronger
U2 - Beautiful Day
U2 - I Still Haven't Found What I'm Looking For
U2 - New Year's Day
U2 - One
U2 - Sunday Bloody Sunday
U2 - With or Without You
Underworld - Born Slippy
Vertical Horizon - Everything You Want
Vertical Horizon - You're a God
Violent Femmes - Blister in the Sun
Weezer - Beverly Hills
Weezer - Buddy Holly
Weezer - My Name Is Jonas
Weezer - Pork And Beans
Weezer - Undone (The Sweater Song)
We The Kings - All Again For You
We The Kings - August Is Over
We The Kings - Check Yes Juliet
We The Kings - Headlines Read Out...
We The Kings - Skyway Avenue
We The Kings - This Is Our Town
We The Kings - Whoa
Yeah Yeah Yeahs - Maps
Yellowcard - Breathing
Yellowcard - Ocean Avenue
Yellowcard - Rock Star Land
```

I'd like to (like the title says) remove all non-unique entries from this list, for example, see how I have this:
```
All Time Low - Dear Maria
All Time Low - Dear Maria, Count Me In
```
I'd like to remove one of them (it doesn't matter which because I'll just be able to change it manually if it's wrong). I'd just like to automate this process to make it easier. It doesn't have to be perfect, just reduce the number of errors in the list, I can manually edit the ones that didn't turn out right.

So, anyone that knows how, can you please point me in the right direction? Tell me what I'll need to do. I'm not asking someone to do all the coding work. I can read up on stuff and figure it out myself.

---

### Post by Can+~ on 2009-09-09
Guessing that the file is sorted, repeated values will be contiguos, and not only that, but character '\n' (CR and/or LF) is before any other alphanumeric character, therefore, you'll always find:

```
something - something
something - something more things
```

Using this assumptions, the algorithm is trivial, go through the text, see if current line has the previous starts with that.

[PHP]#!/usr/bin/env python

playlist = open("songs.txt", "r")

previous = "nothing"
lastmatch = False

for line in playlist:
	# Check if line is the same as previous
	if line.startswith(previous):
		print "Match: a) %s  \n       b) %s" % (previous, line)
		lastmatch = True
	
	# Get the next line if there's no match
	if not lastmatch:
		previous = line.strip()
	
	lastmatch = False[/PHP]

That's as simple as it gets. Also, I added the lastmatch flag, so that if it finds something, it will look again with the same string, in case there are three or more repeated values.

---

### Post by j.bell730 on 2009-09-09
Thank you! That is precisely what I was looking for.

---

