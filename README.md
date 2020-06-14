- Install jackd:
  `sudo apt install jackd`

- Install fluidsynth:
  `sudo apt install fluidsynth`

- Create directory in home folder for user-systemd units:
  `mkdir -p ~/.config/systemd/user`

- Enter the directory:
  `cd ~/.config/systemd/user`

- Create/copy unit files
  **jack.service synth@.service keyboard.service**

- Create/copy synth router file

  `/opt/soundfonts/midi_router.txt`

- download font file

  `cd /opt/soundfonts/`

  `wget http://freepats.zenvoid.org/Piano/YDP-GrandPiano/YDP-GrandPiano-SF2-20160804.tar.bz2`

  `tar -xf YDP-GrandPiano-SF2-20160804.tar.bz2`

  `mv YDP-GrandPiano-SF2-20160804/YDP-GrandPiano-20160804.sf2 YDPGrandPiano.sf2`

  `rm -rf YDP-GrandPiano-SF2-20160804` -

- Enable services

  `systemctl --user enable jack`

  `systemctl --user enable synth`

  `systemctl --user enable keyboard`

- Useful links and commands

````bash
    # Run 'cat /proc/asound/cards' to get a list of audio devices, and modify the grep statement below with a unique identifying string

    # Examples:

    # audioDevice=$(cat /proc/asound/cards | grep "bcm2835_alsa" | awk -F" " '{ print $1 }') # Raspberry Pi on-board audio (high latency - only use if no other options)

    # audioDevice=$(cat /proc/asound/cards | grep "USB-Audio - USB Audio Device" | awk -F" " '{ print $1 }') # Sabrent USB sound card

    # audioDevice=$(cat /proc/asound/cards | grep "USB-Audio - Logitech" | awk -F" " '{ print $1 }') # Logitech USB sound card

    aplay -l

    ```
````
