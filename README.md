[![Made with Python](https://img.shields.io/badge/MADE_WITH-Python3-3776ab.svg)](https://www.python.org/)
[![license](https://img.shields.io/github/license/mashape/apistatus.svg)](https://opensource.org/licenses/MIT)

# M3U8 Downloader

Download the ts files according to the given m3u8 file.

## Usage

```text
m3u8_downloader.py [-h] [-t TIMEOUT] [--ffmpeg-path FFMPEG_PATH]
                   [--ffmpeg-loglevel FFMPEG_LOGLEVEL] [-o OUTPUT] [-y] uri

positional arguments:
  uri                   URI of the m3u8 file

optional arguments:
  -h, --help            show this help message and exit
  -t TIMEOUT, --timeout TIMEOUT
                        timeout used when loading from uri (default None)
  --ffmpeg-path FFMPEG_PATH
                        path to ffmpeg executable (default ffmpeg)
  --ffmpeg-loglevel FFMPEG_LOGLEVEL
                        logging level of ffmpeg (default quiet)
  -o OUTPUT, --output OUTPUT
                        path to output (default output.ts)
  -y, --overwrite       overwrite output files without asking
```

## Dependencies

* **ffmpy**: <https://github.com/Ch00k/ffmpy> - A simplystic FFmpeg command line wrapper.

* **m3u8**: <https://github.com/globocom/m3u8> - Python m3u8 parser.

* **ffmpeg**: <https://ffmpeg.org/> - Used to download, convert and merge the downloaded ts files.

## Dick
1. use chrome to search m3u8 from the video
2. python m3u8_downloader.py  https://baikevideo.cdn.bcebos.com/media/mda-OgJZ5meZEwxyMv5u/e5ee1c791e1ec62761cdf1a852435611.m3u8
3. get the file from current folder
4. convert the file into mp4
# full
ffmpeg -i output.ts -bsf:a aac_adtstoasc -acodec copy -vcodec copy video.mp4

# cut from 23 ~ 44 s
ffmpeg -i output.ts -bsf:a aac_adtstoasc -acodec copy -vcodec copy -ss 00:00:23 -to 00:00:44 video.mp4
