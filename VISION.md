In 2009, I designed, investigated, and built the open-source project I named Jtvlc and distributed binaries for Windows, Mac, and Linux, to allow streaming from VLC, which allowed broadcasters before Twitch existed to broadcast over a million hours to Justin.tv and then Justin.tv allowed viewers to watch, with possibly hundreds or more viewers to watch and chat in each channel. A broadcaster downloaded this CLI that would be started with a username and Justin.tv stream key (not password), and would start VLC on the computer with the correct video encoding parameters and network parameters to point to this local CLI, and then the CLI corrected packets in real-time while broadcasting to Justin.tv servers, to fix bugs that I found in VLC and Wowza (a streaming server) that were different than the protocol standards (summary from Google: RTP (Real-time Transport Protocol) and RTCP (RTP Control Protocol) are companion protocols defined in RFC 3550 that work together to deliver and monitor real-time audio and video streams over IP networks.)

The vision and purpose was that broadcasters might not mind downloading and running a CLI because I provided a binary for Windows, Mac, and Linux, and the broadcasters could also edit the text file to adjust the video parameters sent to VLC. For Justin.tv employees (because this was originally a private repo), I made sure the code has instructions about a workflow on how future Justin.tv engineers could update the project and build the new versions for each platform, similar to how Dropbox built their Windows, Mac, and Linux clients. On the other hand, an unlimited number of streamers could watch each broadcaster's channel, with the normal Justin.tv service without any changes or downloads.

Now of course, it's normal and obvious for streamers to download an app to stream from their computer or other device, but at the time, Justin.tv was one of the most popular streaming websites. Before my project, Justin.tv was happy that users could stream from their computer's face camera, but most users would watch and follow channels on the website without becoming a streamer. Streaming or viewing on Justin.tv simply required using the web browser, and the Adobe Flash plugin was free and often already included with any web browser (see more below).

The CLI also sent a ping every minute to a Heroku database so that a web dashboard on Heroku could show active broadcasters, including an embed of each channel with a screenshot and a link to visit justin.tv/channelname. The number of rows reached over 60 million, and the database size of 5 GB database, causing Heroku to worry about a free Heroku account. That's how I learned that over 1 million broadcaster hours had been streamed using my downloadable CLI (over 60m rows to represent each minute / 60 minutes in an hour is >= 1 million hours of broadcasted channels via Jtvlc in initial months).

This repo is a backup from a random public account, after a new-hire Justin.tv employee made some commits to the internal repo after my summer 2009, and introduced weird comments, and then Justin.tv open-sourced the effort. See my commits by "vlad" which are before their commits.

https://github.com/vladician/jtvlc

Vladislav Yazhbin

AI explains how my Jtvlc project allowed streaming from a file, screen-sharing, and cameras, while Flash was limited to webcams:

Yes, you are completely right. By the summer of 2009, [VLC Media Player](https://images.videolan.org/vlc/) was already heavily utilized as a Swiss Army knife capable of capturing and streaming all three of those sources. [1, 2, 3] 
In July 2009, VideoLAN released VLC 1.0.0 (codenamed "Goldeneye"), which solidified these exact tools. Because VLC operates as a local desktop application rather than being trapped in a web browser's security sandbox like Flash Player, it had full access to system hardware and the operating system.

VLC’s "Open Capture Device" menu in 2009 let you stream:
 
* A File: You could open any media file, DVD, or playlist and broadcast it over a network using built-in streaming wizards. [2] 
* Camera: By mapping to local video capture drivers (like DirectShow on Windows or v4l2 on Linux), VLC could grab a live feed from an integrated webcam or an external capture card and stream it instantly. [4] 
* Screen: Using the screen:// input access module, VLC could treat your entire desktop background as a live media source. Users could point VLC to their own desktop screen, map it to a network port, and stream their entire screen to another computer over protocols like HTTP or UDP. [3, 5, 6, 7] 

While Flash in 2009 struggled with native screensharing from browsers without complex third-party desktop plug-ins, VLC could encode your desktop natively and feed that exact stream into a server (like Wowza or Flash Media Server) to broadcast it out to the web. [1] 
Would you like the exact step-by-step process or the old command-line parameters used back then to stream a desktop screen via VLC?

[1] [https://johnbeales.com](https://johnbeales.com/2008/using-vlc-to-transcode-an-axis-cameras-video-stream-and-stream-it-out-again/)
[2] [https://www.makeuseof.com](https://www.makeuseof.com/vlc-has-been-hiding-a-full-blown-streaming-server-behind-the-play-button/)
[3] [https://crounji.wordpress.com](https://crounji.wordpress.com/2014/04/23/how-to-use-vlc-player-as-screencast-tool-in-windows-mac-and-linux/)
[4] [https://www.reddit.com](https://www.reddit.com/r/VLC/comments/1ilgaun/camera_streaming_vlc/)
[5] [https://www.lifewire.com](https://www.lifewire.com/how-to-capture-a-screencast-using-vlc-2533002)
[6] [https://superuser.com](https://superuser.com/questions/335885/stream-desktop-using-vlc)
[7] [https://stackoverflow.com](https://stackoverflow.com/questions/65293175/how-to-stream-video-using-vlc-in-http-to-other-computer)
