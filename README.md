
# foxbox



# How to create your own foxbox? 

Adapted from this excellent guide on [Full screen kiosk using Debian](https://willhaley.com/blog/debian-fullscreen-gui-kiosk/) 

1. Install debian. The command line version without any desktop environment. 
2. Open a terminal and run `useradd -m foxbox`
3. Update packages `apt-get update`
4. Install new packages 

``` 
   apt-get install \
    sudo \
    xorg \
    chromium \
    openbox \
    lightdm
 
 ```   
 Install firefox 
 
 `apt-get install firefox-esr`
  
 
 With that done, enable autologin in lightdb.conf  (you'll find it in /etc/lightdm/lightdm.conf)
  
  ```
  [SeatDefaults]
  autologin-user=foxbox
  user-session=openbox

  
  ```
  
Restart your system then open a terminal and type `whoami`.If the output shows `foxbox` it means that you were successful in configuring autologin. 
  
  Now create a new openbox config directory 
  
  ```
  mkdir -p $HOME/.config/openbox
  
  ```
  
  Finally create a startup script at $HOME/.config/openbox/autostart 
  
  ```
  nano $HOME/.config/openbox/autostart
  
  
  ```
  
  once that file is open type 
  
  `firefox` 
  
  save changes and exit. 
  
  If you reboot now you should see
  
  
  1. When the system is up you are automatically logged in as foxbox
  2. The system automatically starts firefox 
  
With this setup you have a system running in a single application mode with restricted permissions. Later on we'll see how to enable private browsing by default so that user data is automatically destroyed as soon as he closes his tab. 
  
