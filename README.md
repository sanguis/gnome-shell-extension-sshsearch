SSH Search Provider
=====================
A gnome-shell extension which searches the ssh config and known_hosts file and provides the found ssh connections in your shell overview.

### Features

 * it parses the ~/.ssh/config file and searches for the hostnames
 * it parses the ~/.ssh/known_hosts file and reads all hostnames (to use this feature you have to set the ssh setting "HashKnownHosts" to "no")
 * you are able to define a user for the founded hosts in the search term

### Examples

Assume the ~/.ssh/config file looks like

    Host desktop
    User user
    HostName 192.168.1.100
    
    Host desktop1
    User user
    HostName 192.168.1.101

    host vserver
    User user
    Port 2222
    HostName 11.11.111.111
    
and the ~/.ssh/known_hosts file looks like

    [11.11.111.111]:2222 ssh-rsa AAAAB...
    github.com,207.97.227.239 ssh-rsa AAAAB...
    user.webfactional.com,22.22.222.222 ssh-rsa AAAAB...
    192.168.1.100 ssh-rsa AAAAB...

Here are some example searches and the search results

 * search-term: **desk**
   1. desktop
   2. desktop1
   
 * search-term: **rv**
   1. vserver
   
 * search-term: **11**
   1. 11.11.111.111:2222
   
 * search-term: **97**
   1. 207.97.227.239
   
 * search-term: **user@** (all hostnames are in the search results)
   1. user@desktop
   2. user@desktop1
   3. user@vserver
   4. user@11.11.111.111:2222
   5. user@github.com
   6. user@207.97.227.239
   7. user@user.webfactional.com
   8. user@22.22.222.222
   9. user@192.168.1.100

 * search-term: **user@des**
   1. user@desktop
   2. user@desktop1

### Installation
Install the extension directly from the gnome-shell extension webpage:
https://extensions.gnome.org/extension/73/ssh-search-provider/

or manually

 * copy or link the folder "ssh-search-provider@gnome-shell-extensions.brot.github.com" to ~/.local/share/gnome-shell/extensions
 * enable extension (e.g. via gnome-tweak-tool)

### Selecting Your preferred Terminal Application
At the moment it isn't possible to configure the preferred terminal app directly.
The reason is that gnome-shell in the current stable version (3.2) don't provide
tools for extensions to create extension specific settings. 
With the future version of gnome-shell (3.4) this should be possible and then I 
will provide an updated version of this extension with some gsetting options.

At the moment you could only change the source code directly. So you have to 
change the file ~/.local/share/gnome-shell/extensions/ssh-search-provider@gnome-shell-extensions.brot.github.com/extension.js

Replace 'gnome-terminal' with the name of your preferred terminal app:

    const SSHSEARCH_TERMINAL_APP = 'gnome-terminal';
    
For example

    const SSHSEARCH_TERMINAL_APP = 'terminator';


### License
Copyright (c) 2011 Bernd Schlapsi <brot@gmx.info>

This program is free software: you can redistribute it and/or modify
it under the terms of the GNU General Public License as published by
the Free Software Foundation, either version 3 of the License, or
any later version.

This program is distributed in the hope that it will be useful,
but WITHOUT ANY WARRANTY; without even the implied warranty of
MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
GNU General Public License for more details.

You should have received a copy of the GNU General Public License
along with this program.  If not, see <http://www.gnu.org/licenses/>.
