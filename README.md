# SubtitleParser-CrossPlatform
SubtitleParser for Cross-Platform, Works on iOS, Windows, UWP, Windows Phone, and also works with Xamarin.
thknks to AlexPoint.

Install via NUGET:
,,,
Install-Package Install-Package YunusEfendi.SubtitleParser
,,,

Supported format:
- MicroDvd
- SubRip
- SubStationAlpha
- SubViewer
- TTML
- WebVTT
- Youtube specific XML format (still in development, contribution pleased :) )

How to Use:
# Windows 10 & Windows 10 Mobile (Windows Phone 8.1 same as Windows 10)
```csharp
async Task<StringBuilder> GetSubtitleText(StorageFile storageFile, Encoding encoding)
        {
            var sb = new StringBuilder();
            var parser = new SrtParser();
            using (var stream = await storageFile.OpenStreamForReadAsync())
            {
                var items = parser.ParseStream(stream, encoding);
                foreach (var i in items)
                {
                    foreach (var line in i.Lines)
                    {
                        sb.AppendLine(line);
                    }
                    sb.AppendLine();
                }
            }
            return sb;
        }
