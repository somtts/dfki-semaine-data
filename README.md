# dfki-semaine-data

Speech databases for the British English TTS voices in the [SEMAINE project](http://www.semaine-project.eu/).

## Subsets

There are four speakers, each acting out a character in a specific expressive speaking style.

### Obadiah (male)

Obadiah is gloomy and depressed.

### Poppy (female)

Poppy is outgoing (extraverted) and optimistic.

### Prudence (female)

Prudence is pragmatic and practical.

### Spike (male)

Spike is angry and argumentative.

## Format

The audio data is provided in a single [FLAC](https://xiph.org/flac/) file per subset, recorded at 44.1 kHz sampling frequency with 16 bit per sample.
The textual data is provided in a single [YAML](http://yaml.org/) file per subset.
These files are a list of utterances, each of which contains
- a **prompt** code (file basename),
- the utterance **text**,
- a **date** timestamp (when the recording was created, in [ISO 8601](https://en.wikipedia.org/wiki/ISO_8601) format),
- utterance **start** and **end** times (in seconds) in the FLAC file,
- optionally, the phonetic **segments**, each of which has
    - a **lab**el (based on [SAMPA](http://www.phon.ucl.ac.uk/home/sampa/english.htm), `_` denotes silence), and
    - **end** time (in seconds) _relative to that utterance's **start** time_

For example,
```yaml
- prompt: uni56
  text: Yes.
  date: 2009-06-12T09:59:34Z
  start: 7961.79
  end: 7964.07
  segments:
  - lab: _
    end: 0.99
  - lab: j
    end: 1.07134
  - lab: E
    end: 1.2
  - lab: s
    end: 1.465
  - lab: _
    end: 3.135
```

## Downloading the data

Use the links on the [releases](releases) page.

## Converting the data

For convenience, the utterances for each subset can be be extracted from the YAML and FLAC files using simple commands.
After cloning or downloading and unpacking this repository, run `./gradlew tasks` (or `gradlew tasks` on Windows) for details.

### Prerequisites

You will need [Java](https://www.java.com/) to run the conversion tasks. Extracting the utterances to WAV files also requires [`sox`](http://sox.sourceforge.net/) to be installed.
