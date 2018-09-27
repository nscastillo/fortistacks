# Automate Secured SDWAN demo

The goal is to deliver a automated deployment of:
 - a media server
 - 2 network simulating
    * bad WAN 
    * guaranteed network like MPLS.
 - 2 simulated branches with Fortigate SDWAN firewalls.
 
 ## Scenario
 
 Entreprise A want to organize a live broadcasted townhall. The IT must rapidely deploy a media server and ensure proper bandwidth and latency to ensure smooth upload and broadcasts.
 Presented that way SDWAN rules must be changed on the time of the broadcast for video delivery and resumed to business critical apps at the end of it.
 
 
 ## Steaming
 
 Using OBS and do those settings
 https://github.com/ant-media/Ant-Media-Server/wiki/Reduce-Latency-in-RTMP-to-HLS-Streaming
 
 To watch the stream:
 http://<SERVER_NAME>/LiveApp/streams/<STREAM_ID>.m3u8 HLS
 
 See this https://github.com/ant-media/Ant-Media-Server/wiki/Play-Live-and-VoD-Streams for details
 
 In community edition, MP4 URL will be available in this URL http://<SERVER_NAME>:5080/LiveApp/streams/<STREAM_ID>.mp4

Embeded player is available here:
http://<SERVER_NAME>:5080/LiveApp/play.html?name=<STREAM_ID> 

For demos might want to broadcast a file with vlc:
 cvlc  -vvv FILE016.MP4 --sout '#transcode{vcodec=h264,scale=Auto,width=1280,height=720,acodec=mp3,ab=128,channels=2,samplerate=44100}:std{access=rtmp,mux=ffmpeg{mux=flv},dst=rtmp://a.rtmp.youtube.com/live2/stream-name}'
src: https://stackoverflow.com/questions/40428837/broadcasting-to-youtube-live-via-rtmp-using-vlc-from-terminal
 
 As the VOD usually buffer the file hence the network lag are not visibles
 Broadasting and viewing from same pc overflow the bandwidth