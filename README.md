# rssgenerator
This is more of a tutorial than a repository.  The idea here is to create a way to easily generate the xml code for new episodes of my podcast.  I do this using a simple google form combined with code in google sheets to generate the xml code. Once generated I maually paste these code blocks into the RSS feed for my podcast.  I then upload the audio file and image to the episodes and images folders (respectively) on the server.

Step one is to set up a google form to collect the data:
The questions could be in any order, but this is how they are set up for my form and spreadsheet.  The column they appear in in my spread sheet is also listed.  If you change which column your data goes to be sure to change it in the code below as well!

<ul>
  <li>Episode Number (colum K in my sheet)
  <li>Title of Podcast Episode (column B)
  <li>Description (column C)
  <li>exact file name of audio file (column D)
  <li>length in bytes (column E)
  <li>Day (3 letter abbreviation, (for spotify you need to capitolize the first letter only) I use radio buttons for this question in the form) (column F)
  <li>Date (dd) (column G)
  <li>Month (three letter code)(for spotify you need to capitolize the first letter only) (column H)
  <li>Year (yyyy) (column I)
  <li>Length (hr:mn:sc) (column J)
  </ul>
  In the google sheet where your responsed are recoreded past the following code at the end of the row. (Replace url with your own url of course!)
  
  Whenever you need to add a new episde, just fill out the form, then go to your google sheet where the responses are stored.  Click in the lower right corner of the code cell from the previous episode and drag down.  Google sheets will auto poulate with the correct row number for the episode and generate the xml for your episode.  Note, episode 1 will be in row 2 because row 1 contains your column headings.
  


=CONCATENATE("<item> <itunes:episodeType>full</itunes:episodeType><itunes:episode>",K3,"</itunes:episode><title>", B2,"</title> <itunes:summary>", C2,"</itunes:summary> <description><content:encoded><![CDATA[", C2, "<br><a href=""https://daniel.jessica-lily.com/index.html"">The Didi Chronicles</a>]]></content:encoded></description> <link>https://daniel.jessica-lily.com/index.html</link> <enclosure url=""https://daniel.jessica-lily.com/episodes/", D2,""" type=""audio/mpeg"" length=""", E2, """></enclosure> <pubDate>", F2, ", ", G2, " ", H2, " ", I2, " ", "12:01:01+0000</pubDate> <itunes:duration>", J2, "</itunes:duration> <itunes:explicit>no</itunes:explicit> <guid>https://daniel.jessica-lily.com/episodes", D2, "</guid> </item>")
  
With the above code my output looks like this: 

<item> <itunes:episodeType>full</itunes:episodeType><itunes:episode>1</itunes:episode><title>testrun1</title> <itunes:summary>systems test</itunes:summary> <description><content:encoded><![CDATA[systems test<br><a href="https://daniel.jessica-lily.com/index.html">The Didi Chronicles</a>]]></content:encoded></description> <link>https://daniel.jessica-lily.com/index.html</link> <enclosure url="https://daniel.jessica-lily.com/episodes/testrun1.mp3" type="audio/mpeg" length="1195280"></enclosure> <pubDate>Sat, 08 Feb 2020 12:01:01+0000</pubDate> <itunes:duration>0:0:30</itunes:duration> <itunes:explicit>no</itunes:explicit> <guid>https://daniel.jessica-lily.com/episodestestrun1.mp3</guid> </item>
  
