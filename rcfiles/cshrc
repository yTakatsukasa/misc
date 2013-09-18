setenv LANG C
unset autologout
setenv LD_LIBRARY_PATH ""
setenv HOST_SHORT `hostname | cut -f 1 -d .`
set path=(/usr/local/sbin /usr/local/bin /sbin /bin /usr/sbin /usr/bin )
if ( $?SSH_CLIENT && `env LANG=C tty` == "not a tty" ) then
	setenv MANPATH	/usr/man:/usr/share/man
	setenv LD_LIBRARY_PATH /lib:/usr/lib
    setenv LANG ja_JP.UTF-8
	exit
endif
if ( ! $?DISPLAY && $?REMOTEHOST ) then
	setenv DISPLAY "$REMOTEHOST":0.0
endif

if ( `tty` != "not a tty" ) then
    stty -istrip cs8 -parenb
    stty erase "^H"
endif
tty | grep /dev/tty > /dev/null
if ( $? ) then
    setenv LANG ja_JP.UTF-8
endif

bindkey "^P" "history-search-backward"
bindkey "^N" "history-search-forward"
set prompt = "${USER}@${HOST_SHORT}:%~% "
set color
set autolist
set savehist = (10000 merge)
set ignoreeof

umask 002
limit stacksize 81920

#setenv LANG ja_JP.euc
#setenv LANG ja_JP.eucJP
#setenv LANG ${SUPPORTED}
alias view 'vim -R'
alias grep 'egrep -n --color=auto'
alias cgrep 'egrep -n --color=always'
alias lv   'lv -c'
alias w		'w | sort'
setenv SVN_EDITOR vim
which screen  >& /dev/null
if( $? == 0 ) then
    if( $?TERM == 1 ) then
        if( $TERM != "screen" ) then
            set screen_list = `/usr/bin/env screen -ls | \grep Detached`
            echo $screen_list
            echo ""
        endif
    endif
endif
