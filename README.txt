1. Create the following tables in ORACLE.

create table song (song_id integer primary key,
		song_title varchar2(255),
		song_genre varchar2(255),
		play_count integer,
		duration integer,
		cluster_id varchar2(30) );



create table user_system (user_id varchar2(30) primary key,
		first_name varchar2(255),
		last_name varchar2(255),
		age integer,
		gender varchar2(255),
		native_language varchar2(30),
		password varchar2(255),);



create table artist (artist_id integer primary key,
		artist_name varchar2(255),
		popularity integer,
		genre varchar2(255));



create table instrument (instrument_id integer primary key,
		instrument_name varchar2(255));



create table user_to_song (song_id integer references song(song_id),
		user_id varchar2(30) references user_system(user_id),
		cluster_id varchar2(30));



create table artist_to_song (artist_id integer references artist(artist_id),
		song_id integer references song(song_id));



create table instrument_to_song (instrument_id integer references instrument(instrument_id),
		integer references song(song_id));


create table user_to_instrument (user_id varchar2(60) references user_system(user_id),
		      instrument_id integer references instrument(instrument_id));


2. Load the CSV files into corresponding tables in oracle.

3. Install wamp and open the folder "wamp" and place the following files in the folder named "www" (wamp -> www).
	
	a.LikeHit
	b.login
	c.RefreshHit

4. Make sure WAMP is running by ensuring the color of the "W" icon is green in the system tray.

5. Place all the files "index.html", the folder "images" and the file "quad.css" in any folder.

6. Use Chrome browser and disable web security by doing the following (To allow AJAX to function):
	a. Right click on chrome shortcut -> Properties
	b. Paste  --disable-web-security, in the end of the TARGET field.
		eg. "C:\Program Files (x86)\Google\Chrome\Application\chrome.exe" --disable-web-security
   	(This workaround is only to overcome the "Same-origin" policy on local machine. In reality, when these files are hosted on the 		website, all files will	belong to the same site so they will work without any issues.)

7. Launch Chrome by clicking the shortcut and you should see a warning about the security when you open chrome.

8. Now launch the index.html file on chrome. 

9. Existing users can login with their login credentials and the song suggestions will already be present. If you are a new user, just       enter your name in the login field and enter the password you'd like. If the username already exists, the error "Invalid       Credentials" will appear and you'll have to choose a different username. Once you enter the new username and password, you                will be registered and the following will be displayed on the screen - "Welcome new user UNAME". Since the system does not know    about the type of music liked by the user, there are no song suggestions initially. However random tracks are displayed on              screen. Based on the random songs that were liked by the user, songs are suggested to the user during their next login attempt or         when he refreshes the suggestions.      

10. The suggestions improve when the user hits the LIKE button against the songs displayed in the SUGGESTIONS area (However, there is no indication on screen, that the like button has been clicked). 

11. Random tracks are also displayed in order to help the user discover new music. If the user likes the random songs, the song suggestions will improve accordingly.