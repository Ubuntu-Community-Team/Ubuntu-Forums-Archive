---
title: "LUA and Conky"
date: 2010-11-03
forum: Programming Talk
---

### Post by SOG420 on 2010-11-03
I'm just now learning programming and I decided to start with LUA. Any sites you can recommend on tutorials not just based on WOW would be appreciated. My problem  is when I put a LUA script path it doesn't recognize it being there.
 Here is my .conkyrc file:

background no
update_interval 1
total_run_times 0
own_window yes
own_window_transparent yes
own_window_class Conky
own_window_hints undecorate,sticky,skip_pager,skip_taskbar,below
double_buffer yes
no_buffers yes
text_buffer_size 2048
cpu_avg_samples 2
net_avg_samples 2
override_utf8_locale yes
draw_shades no
draw_outline no
draw_borders no
draw_graph_borders yes
use_spacer none
minimum_size 1300 0
alignment bottom_left
gap_x 12
gap_y 12
uppercase no
use_xft yes
xftfont Gputeks-Bold:size=12
xftalpha 0.8
default_color ffffff

lua_load </scripts/EOW>

 

TEXT
${lua_parse string_function}
${lua_bar int_function}
${lua_gauge int_function}
${lua_graph int_function}
${color}Name              PID    CPU%   MEM%
${lua_read_parse top_cpu_colour  ${top name 1} ${top pid 1} ${top cpu 1} ${top mem 1}}
${lua_read_parse top_cpu_colour  ${top name 2} ${top pid 2} ${top cpu 2} ${top mem 2}}
${lua_read_parse top_cpu_colour  ${top name 3} ${top pid 3} ${top cpu 3} ${top mem 3}}
${lua_read_parse top_cpu_colour  ${top name 4} ${top pid 4} ${top cpu 4} ${top mem 4}}
${color}Mem usage
${lua_read_parse top_mem_colour  ${top_mem name 1} ${top_mem pid 1} ${top_mem cpu 1} ${top_mem mem 1}}
${lua_read_parse top_mem_colour  ${top_mem name 2} ${top_mem pid 2} ${top_mem cpu 2} ${top_mem mem 2}}
${lua_read_parse top_mem_colour  ${top_mem name 3} ${top_mem pid 3} ${top_mem cpu 3} ${top_mem mem 3}
${voffset 100}${font Gputeks-Bold:size=24}${time %A}, ${time %d} ${time %B} ${time %Y}${font}
${goto 900}${font Gputeks-Bold:size10}${execi 1800 conkyEmail -m POP -s pop.gmail.com -e ssl -u william9000 -p XXX -i 2}${if_running audacious2}
${goto 900}${font Gputeks-Bold:size10}${color ffffff}AUD:${color ffffff} ${exec audtool --current-song | cut -b-34}
${goto 900}${font Gputeks-Bold:size10}${color ffffff} ${exec audtool --current-song-bitrate-kbps} kbps * ${exec audtool --current-song-length} ${goto 900}${font Gputeks-Bold:size10}$execbar expr 100 \* $(audtool --current-song-output-length-seconds) \/ $(audtool --current-song-length-seconds)}${color ffffff}${hr 2}$endif
${voffset -90}${font route3:size=160}${time %l}${font route3:size=100}${voffset -80}${goto 230}${time %M}${font}
${voffset 200}${execpi 360 conkyForecast --location=USKY1108 --imperial --template=/usr/share/conkyforecast/conkyForecast.template}

and this being the script:
-- Conky Lua scripting example
--
-- In your conkyrc, use ${lua string_func} to call conky_string_func(), ${lua
-- int_func} to call conky_int_func(), and so forth.  You must load this script
-- in your conkyrc using 'lua_load <path>' before TEXT in order to call the
-- function.
--
do
	-- configuration
	local interval = 5 

	-- local variables protected from the evil outside world
	local next_update
	local buf 
	local int = 0
	local colour = 0
	local function update_buf()
		buf = os.time()
	end

	-- a function that returns the time with some special effects using a 5
	-- second interval
	function conky_string_func()
		local now = os.time()

		if next_update == nil or now >= next_update then
			update_buf();
			next_update = now + interval
		end
		colour = colour + 11100

		return string.format("${color #%06x}The time is now ", colour%0xffffff) .. tostring(buf) .. "${color}"
	end

	-- this function changes Conky's top colour based on a threshold
	function conky_top_colour(value, default_colour, upper_thresh, lower_thresh)
		local r, g, b = default_colour, default_colour, default_colour
		local colour = 0
		-- in my case, there are 4 CPUs so a typical high value starts at around ~20%, and 25% is one thread/process maxed out
		local thresh_diff = upper_thresh - lower_thresh
		if (value - lower_thresh) > 0 then
			if value > upper_thresh then value = upper_thresh end
			-- add some redness, depending on the 'strength'
			r = math.ceil(default_colour + ((value - lower_thresh) / thresh_diff) * (0xff - default_colour))
			b = math.floor(default_colour - ((value - lower_thresh) / thresh_diff) * default_colour)
			g = b
		end
		colour = (r * 0x10000) + (g * 0x100) + b -- no bit shifting operator in Lua afaik

		return string.format("${color #%06x}", colour%0xffffff)
	end
	-- parses the output from top and calls the colour function
	function conky_top_cpu_colour(arg)
		-- input is ' ${top name 1} ${top pid 1} ${top cpu 1} ${top mem 1}'
		local cpu = tonumber(string.match(arg, '(%d+%.%d+)'))
		-- tweak the last 3 parameters to your liking
		-- my machine has 4 CPUs, so an upper thresh of 25% is appropriate
		return conky_top_colour(cpu, 0xd3, 25, 15) .. arg
	end
	function conky_top_mem_colour(arg)
		-- input is '${top_mem name 1} ${top_mem pid 1} ${top_mem cpu 1} ${top_mem mem 1}'
		local mem = tonumber(string.match(arg, '%d+%.%d+%s+(%d+%.%d+)'))
		-- tweak the last 3 parameters to your liking
		-- my machine has 8GiB of ram, so an upper thresh of 15% is appropriate
		return conky_top_colour(mem, 0xd3, 15, 5) .. arg
	end

	-- returns a percentage value that loops around
	function conky_int_func()
		int = int + 1
		return int % 100
	end
end

I get this:
Conky: llua_load: cannot open </scripts/EOW>: No such file or directory
Conky: unknown variable lua_read_parse
Conky: unknown variable lua_read_parse
Conky: unknown variable lua_read_parse
Conky: unknown variable lua_read_parse
Conky: unknown variable lua_read_parse
Conky: unknown variable lua_read_parse
Conky: unknown variable lua_read_parse
Conky: got an endif without matching if
***** Imlib2 Developer Warning ***** :
	This program is calling the Imlib call:

	imlib_context_free();

	With the parameter:

	context

	being NULL. Please fix your program.
Thanks for any help

---

