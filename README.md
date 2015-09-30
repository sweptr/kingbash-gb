# kingbash-gb
Menu drive auto-completion for bash terminals under X

One of the things i really missed from my glorious amigaos system was the kingcon terminal emulator.
It featured a simple and useful file browser when autocompletion was requested.
Now i managed to get something similar for bash too.


Mandatory requirements:
-----------------------------
  * Gambas 3 (usually the very latest version)
  * Qt4
  * An X terminal running bash


Compiling it:
-----------------------------
After you installed gambas 3, just checkout and compile xt7 that way:

# git clone https://github.com/kokoko3k/kingbash-gb
# cd kingbash-gb/
# /path/to/gambas/binaries/gbc3 -e -a -g -t -p -m
# /path/to/gambas/binaries/gba3
# (This will create ./kingbash-gb.gambas)

Installation:
-----------------------------
# The compile stage created a file named ./kingbash-gb.gambas
# cp -a ./kingbash-gb.gambas /usr/local/bin/
# Next, append the following to your ~/.bashrc:


	kingbash.gb() {
	    OUTPUT=$(/usr/bin/kingbash.gambas "$READLINE_LINE" "$READLINE_POINT")
	    READLINE_POINT=$(echo "$OUTPUT"|tail -n1)
	    READLINE_LINE=$(echo "$OUTPUT"|head -n1)
	}
	
	if  [ "$DISPLAY"  != "" ]; then
	        #bind -x '"\C-e": kingbash'     #for Use with Ctrl-e
	        bind -x '"\t": kingbash'        #for Use with Tab
	fi


Check:
-----------------------------
Login to another X terminal running bash and try auto-completion via <TAB> key.
You should see a window inside the current one that will allow you to select auto-completed items.


