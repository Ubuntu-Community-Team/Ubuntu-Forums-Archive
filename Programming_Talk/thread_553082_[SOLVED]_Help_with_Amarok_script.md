---
title: "[SOLVED] Help with Amarok script"
date: 2007-09-17
forum: Programming Talk
---

### Post by kbzona on 2007-09-17
Ive found this script for amarok.. its an A-B repeat script, but i need a little bit more accuracy in the script, because this plugins loops only in   seconds, but i also need that loop in miliseconds... for example

i have a song that i need to loop, but with the current plugin i can just make:   00:45 - 00:50   but what i  need is 00:45.3 - 00:50.12

Here is the code:

```
#!/usr/bin/env ruby

require 'timeout'

MenuItemName = "Repeat A/B"
Integer a = 0
Integer b = 0
Integer diff = 0
needAbreak = false
file = nil

def cleanup()
	`dcop amarok script removeCustomMenuItem #{MenuItemName}`
end
trap( "SIGTERM" ) { cleanup() }

def cleanVar()
	a = 0
	b = 0
	diff = 0
	needAbreak = false
	file = nil
end

`dcop amarok script addCustomMenuItem #{MenuItemName}` #Insert menu item

loop do
	needAbreak = false
	message = gets().chomp() #Read message from stdin
	command = /[A-Za-z]*/.match( message ).to_s()

	case command
		when "configure"
			msg  = "This script does not have configuration options."
			`dcop amarok playlist popupMessage "#{msg}"`
#First click
		when "customMenuClicked"
			a = `dcop amarok player trackCurrentTime`.to_i() #A
			`dcop amarok playlist popupMessage "a=#{a} seconds"` #Display
			file = `dcop amarok player path`.to_s()
#second click
			loop do
				if /[A-Za-z]*/.match( gets().chomp() ).to_s() == "customMenuClicked"
					if `dcop amarok player path`.to_s() != file 
						needAbreak = true
						break #Track changed
					end

					b = `dcop amarok player trackCurrentTime`.to_i() #B
					`dcop amarok playlist popupMessage "b=#{b} seconds"` #Display

					if b < a #Scrollbar
						needAbreak = true
					else diff=b-a #How long do we have to wait until repeat
					end

					break
				end
			end

			if needAbreak == true #Track or scrollbar changed
				`dcop amarok playlist popupMessage "Track changed or time flows backwards"`
				cleanVar() #Clean up for the next run
				next #We are done
			end
#Loop
			`dcop amarok player seek #{a}` #Jump to A - First repeat

			loop do #Loop A-B until third click or file change
				begin #every "diff" seconds jump back to A
					Timeout::timeout(diff) {
						loop do #we have to wait here; so look for clicks
							if /[A-Za-z]*/.match( gets().chomp() ).to_s() == "customMenuClicked"
								needAbreak = true
								break
							end

						end
					}
				rescue TimeoutError
					if `dcop amarok player path`.to_s() != file
						cleanVar() #Clean up for the next run
						break #User changed track; we are done
					elsif `dcop amarok player trackCurrentTime`.to_i() < a or `dcop amarok player trackCurrentTime`.to_i() > b+2
						cleanVar() #Clean up for the next run
						break #User moved scrollbar
					else 
						`dcop amarok player seek #{a}` #Repeat
					end
				end

				if needAbreak == true
					cleanVar() #Clean up for the next run
					break #We are done
				end
			end
	end
end

```


thnx in advance

---

### Post by kbzona on 2007-09-18
help please :(:(

i was playing with the script but i cant do what i want...

ive changed Integers to Float and trackCurrentTime to trackCurrentTimeMs but didnt work...

---

### Post by kbzona on 2007-09-27
nevermind... ive found that mplayer can do this way better than that amarok script... :)

---

