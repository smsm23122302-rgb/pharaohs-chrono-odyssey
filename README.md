# pharaohs-chrono-odyssey
```react
import React, { useState, useEffect } from 'react';
import { 
  Hourglass, BookOpen, Clock, Compass, Shield, Zap, Sparkles, ChevronRight, 
  Award, Key, Play, Pause, X, Layers, User, Bookmark, Feather, Scroll, 
  Eye, CheckCircle, ChevronDown, RefreshCw, Star, Heart
} from 'lucide-react';

// Custom Regal Egyptian-Chrono Avatar Badges with Detailed Styling
const RegalAvatar = ({ type, name }) => {
  const getBadgeStyle = () => {
    switch (type) {
      case 'ahmed':
        return {
          bg: "from-amber-600 via-yellow-500 to-amber-900",
          border: "border-amber-400",
          glow: "shadow-[0_0_25px_rgba(245,158,11,0.5)]",
          symbol: "𓋹", // Ankh
          sub: "Chrono-Nomad"
        };
      case 'khaled':
        return {
          bg: "from-amber-800 via-amber-700 to-amber-950",
          border: "border-amber-500",
          glow: "shadow-[0_0_20px_rgba(217,119,6,0.4)]",
          symbol: "𓇳", // Sun Ra
          sub: "1971 Father"
        };
      case 'drYoussef':
        return {
          bg: "from-cyan-700 via-sky-800 to-slate-900",
          border: "border-cyan-400",
          glow: "shadow-[0_0_20px_rgba(6,182,212,0.4)]",
          symbol: "𓁹", // Eye of Horus
          sub: "Scientist"
        };
      case 'alMahir':
        return {
          bg: "from-amber-900 via-zinc-800 to-stone-900",
          border: "border-amber-600",
          glow: "shadow-[0_0_18px_rgba(180,83,9,0.3)]",
          symbol: "𓌢",
          sub: "Master Mechanic"
        };
      case 'karim':
        return {
          bg: "from-sky-900 via-indigo-950 to-slate-950",
          border: "border-sky-400 animate-pulse",
          glow: "shadow-[0_0_25px_rgba(56,189,248,0.5)]",
          symbol: "𓂻",
          sub: "Running Shadow"
        };
      case 'ghost':
        return {
          bg: "from-cyan-900 via-blue-950 to-purple-950",
          border: "border-cyan-300",
          glow: "shadow-[0_0_25px_rgba(103,232,249,0.6)]",
          symbol: "𓅓",
          sub: "Temporal Entity"
        };
      case 'guardians':
        return {
          bg: "from-slate-950 via-amber-950 to-black",
          border: "border-amber-500",
          glow: "shadow-[0_0_20px_rgba(217,119,6,0.5)]",
          symbol: "𓃦", // Anubis / Jackal
          sub: "Thief Enforcers"
        };
      case 'singer':
        return {
          bg: "from-pink-900 via-rose-950 to-purple-950",
          border: "border-pink-400",
          glow: "shadow-[0_0_20px_rgba(244,63,94,0.4)]",
          symbol: "𓏢",
          sub: "Cleopatra Songstress"
        };
      case 'omar':
        return {
          bg: "from-indigo-900 via-purple-950 to-slate-900",
          border: "border-indigo-400",
          glow: "shadow-[0_0_20px_rgba(129,140,248,0.4)]",
          symbol: "𓀞",
          sub: "1974 Performer"
        };
      case 'hossam':
        return {
          bg: "from-slate-800 via-slate-900 to-black",
          border: "border-slate-400",
          glow: "shadow-[0_0_15px_rgba(148,163,184,0.3)]",
          symbol: "𓍝",
          sub: "BMW Supervisor"
        };
      default:
        return {
          bg: "from-amber-700 to-amber-950",
          border: "border-amber-400",
          glow: "shadow-[0_0_15px_rgba(245,158,11,0.3)]",
          symbol: "𓋹",
          sub: "Character"
        };
    }
  };

  const style = getBadgeStyle();

  return (
    <div className={`relative w-28 h-28 md:w-32 md:h-32 rounded-full border-2 ${style.border} ${style.glow} p-1 bg-slate-950 flex flex-col items-center justify-center transition-transform duration-300 hover:scale-105`}>
      <div className={`w-full h-full rounded-full bg-gradient-to-br ${style.bg} flex flex-col items-center justify-center relative overflow-hidden border border-white/20`}>
        {/* Hieroglyphic Motif Background */}
        <span className="absolute inset-0 flex items-center justify-center text-5xl md:text-6xl text-amber-200/20 font-serif select-none pointer-events-none">
          {style.symbol}
        </span>
        
        {/* Inner Core Symbol */}
        <div className="z-10 text-2xl md:text-3xl text-amber-300 drop-shadow-[0_2px_8px_rgba(0,0,0,0.8)] font-serif">
          {style.symbol}
        </div>
        <span className="z-10 text-[9px] font-bold tracking-widest text-white/90 uppercase mt-1 px-1 text-center truncate w-full">
          {name.split(' ')[0]}
        </span>
      </div>
    </div>
  );
};

const App = () => {
  // Navigation & Page State
  const [activePage, setActivePage] = useState('home'); // 'home', 'intro', 'summary', 'characters', 'chapters', 'literary', 'creators'
  const [selectedCharacter, setSelectedCharacter] = useState(null);
  const [selectedChapter, setSelectedChapter] = useState(0);
  const [selectedEra, setSelectedEra] = useState('1971');
  const [isPreorderOpen, setIsPreorderOpen] = useState(false);
  const [isBookmarked, setIsBookmarked] = useState(false);
  const [readingProgress, setReadingProgress] = useState(1);
  const [copiedNotification, setCopiedNotification] = useState(false);

  // Characters Data
  const charactersList = [
    {
      id: 'ahmed',
      name: 'Ahmed El-Sayed',
      role: 'The Chrono-Nomad',
      title: 'Car Technician & Temporal Anchor',
      era: 'Present (2025) & Multiverse Traveler',
      type: 'ahmed',
      quote: "I wasn't being pulled into time anymore. Time was turning toward me.",
      fullDesc: "A quiet car technician working at a BMW workshop in Alexandria. His ordinary life dissolves when he unearths an ancient metallic watch in an automobile glove compartment. Bound to a 92% Temporal Resistance Index (Subject Code T-013), Ahmed transforms from a hesitant mechanic into humanity's ultimate counterweight against cosmic time-pruning architectures."
    },
    {
      id: 'khaled',
      name: 'Khaled Nour',
      role: "Ahmed's Father",
      title: 'Electronics Technician',
      era: '1971 Timeline',
      type: 'khaled',
      quote: "The things I hoped would never return... destiny has already chosen.",
      fullDesc: "Encountered by Ahmed in 1971 Alexandria as a young, resilient man seeking electronics work. Khaled unknowingly carries altered genetic structures making him compatible with memory transfers, binding his bloodline to the ancient Chrono Ankh Key."
    },
    {
      id: 'drYoussef',
      name: 'Dr. Youssef / Mounir Sadiq',
      role: 'The Scientist',
      title: 'Master of Chrono-Physics',
      era: 'Research Facility & Present',
      type: 'drYoussef',
      quote: "Time is not a road you can walk blindly. You need a map, a compass, and a counterweight.",
      fullDesc: "A brilliant scientist operating out of a laboratory where modern quantum instruments collide with ancient papyrus fragments. He guides Ahmed through the mysteries of the Chrono Key and calculates the orbital shifts between Authority and Contingency."
    },
    {
      id: 'alMahir',
      name: 'Al-Mahir',
      role: 'Old Master Mechanic',
      title: 'Keeper of Mechanical Wisdom',
      era: '1971 Secret Workshop',
      type: 'alMahir',
      quote: "You're chasing the version of yourself you were never allowed to become.",
      fullDesc: "An old master mechanic in the secret 1971 underground workshop. He instructs Ahmed in both engine mechanics and temporal defense techniques, preparing him to face the creeping shadows."
    },
    {
      id: 'karim',
      name: 'Karim',
      role: "Ahmed's Brother",
      title: 'The Running Shadow & Echo',
      era: 'Disappeared / Alternate Timeline',
      type: 'karim',
      quote: "I don't run from you... I run because of you.",
      fullDesc: "Ahmed's brother who vanished in the present day. His living echo glides across past timelines—his shadow briefly detaching from his feet—acting as a catalyst for Ahmed's pursuit of truth."
    },
    {
      id: 'ghost',
      name: 'Chrono Ghost',
      role: 'Temporal Entity',
      title: 'Workshop Cosmic Sentinel',
      era: '1971 Workshop',
      type: 'ghost',
      quote: "Bearer of the Echo, state your purpose before the gears of history.",
      fullDesc: "A radiant, translucent entity encountered in the 1971 workshop. Formed from fractured chronal energy, it tests travelers who dare to manipulate the timeline."
    },
    {
      id: 'guardians',
      name: 'The Thief Guardians',
      role: 'Ancient Enforcers',
      title: 'Jackal-Masked Sentries',
      era: 'Ancient Tombs & Timelines',
      type: 'guardians',
      quote: "Time does not like being disturbed... it demands a toll in certainty.",
      fullDesc: "A mysterious order wearing Jackal masks who guard the sacred tomb chambers, ancient traps, and scattered Ankh fragments against unworthy seekers."
    },
    {
      id: 'singer',
      name: 'Janitor / Singer',
      role: 'Disco Cleopatra Performer',
      title: 'Voice of the Echoes',
      era: '1974 Cairo',
      type: 'singer',
      quote: "Fear creates cruelty, not truth. Let the song be heard.",
      fullDesc: "A young woman working at Disco Cleopatra in 1974 Cairo. Mocked by crowds, she finds her voice through Ahmed's encouragement, transforming mockery into resounding applause."
    },
    {
      id: 'omar',
      name: 'Omar',
      role: "Ahmed's Friend",
      title: 'Aspiring Stage Performer',
      era: '1974 Cairo',
      type: 'omar',
      quote: "Breathe. You are not alone in this age.",
      fullDesc: "Ahmed's vibrant friend in 1974 Cairo who freezes on stage. Ahmed's intervention gives Omar the courage to perform, forming the second Time Key."
    },
    {
      id: 'hossam',
      name: 'Hossam',
      role: 'BMW Workshop Supervisor',
      title: 'Senior Service Manager',
      era: 'Present Day (Alexandria)',
      type: 'hossam',
      quote: "Ahmed! The engine is still not opened! Open it now!",
      fullDesc: "Ahmed's pragmatic, loud supervisor at the BMW Service Center in modern Alexandria, representing the rigid routine of ordinary life before time fractured."
    }
  ];

  // Novel Chapters & Text Extracts
  const chapterData = [
    {
      num: 1,
      title: "The Broken Watch",
      era: "2025 Alexandria -> 1971",
      keys: 3,
      vocab: [
        { word: "Ambition", def: "A strong desire to achieve greatness or goal" },
        { word: "Engraved", def: "Inscribed or carved deeply into metal/stone" },
        { word: "Resemble", def: "To look like or possess similar qualities" },
        { word: "Discipline", def: "Self-control and structured focus" }
      ],
      summary: "Ahmed El-Sayed leads an uninspired life at a BMW service center in Alexandria. Lifting the hood of an old car, he finds a heavy, scratched metallic watch engraved with alien glyphs. Upon locking it to his wrist, reality folds. He lands in 1971 Alexandria, meeting his father Khaled as a young job-seeker. By fixing a broken radio and fighting off thieves, Ahmed earns his first three Time Keys.",
      excerpt: "Ahmed El-Sayed lived a quiet life that felt louder inside his mind than it ever looked from the outside. Every single morning he woke up with the strange feeling that time was moving forward without him while he remained stuck in the same place. When he lifted the hood, he noticed an old metallic watch that did not belong to this time. It tightened painfully, and the world around him folded inward. When he opened his eyes, he stood in 1971..."
    },
    {
      num: 2,
      title: "The City of Echoes",
      era: "1974 Cairo",
      keys: 3,
      vocab: [
        { word: "Activated", def: "Engaged or set into motion" },
        { word: "Pulsed", def: "Vibrated or throbbed with energetic rhythm" },
        { word: "Mockery", def: "Scornful ridicule or teasing behavior" },
        { word: "Possessed", def: "Held, controlled, or owned" }
      ],
      summary: "The watch activates, sending Ahmed to Cairo in 1974 outside Disco Cleopatra, dressed in 70s bell-bottoms. He helps his friend Omar conquer stage panic, solves a stolen necklace crime, and stands up for a mocked young singer. Earning three more Time Keys, Ahmed gains social confidence, eloquence, and leadership.",
      excerpt: "Ahmed looked down at his clothes and sighed. He was wearing bell-bottom pants and a shiny shirt. 'I hate time travel,' he muttered. Inside Disco Cleopatra, Omar froze on stage while people laughed. Ahmed stepped forward: 'Stop laughing. Breathe. You're not alone.' Silence turned into applause..."
    },
    {
      num: 3,
      title: "The Running Shadow",
      era: "Downtown Cairo & Workshop",
      keys: 3,
      vocab: [
        { word: "Distorted", def: "Twisted or warped out of normal shape" },
        { word: "Emerged", def: "Came out or became visible" },
        { word: "Fractured", def: "Broken into distinct fragments" },
        { word: "Materialized", def: "Appeared physical and tangible" }
      ],
      summary: "Ahmed pursues a mysterious boy through downtown Cairo whose steps glide and whose shadow detaches from his feet. Time turns liquid; taxis melt like holograms. Stepping through a blue portal into Al-Mahir's secret underground workshop, Ahmed fights shadow creatures and learns he is chasing a version of himself he was never permitted to become.",
      excerpt: "The boy didn't run—he glided, his shadow detached from his feet for a moment before reconnecting. Time had become liquid. The watch pulsed like a heartbeat. Al-Mahir turned to him: 'You're not chasing a boy. You're chasing the version of yourself you were never allowed to become.'"
    },
    {
      num: 4,
      title: "The Hospital of Truth",
      era: "Alexandria General Hospital",
      keys: 3,
      vocab: [
        { word: "Synchronized", def: "Coordinated in exact time" },
        { word: "Precise", def: "Exact, accurate, and mathematical" },
        { word: "Protest", def: "Refusal or strong objection" },
        { word: "Analytical", def: "Logical, systematic, and investigative" }
      ],
      summary: "Arriving at Alexandria General Hospital, Ahmed discovers a sinister restricted wing where human memories are harvested into glowing liquid tanks. Finding his family name in files, he destroys the extraction machinery and rescues patients, gaining heightened analytical thinking.",
      excerpt: "Inside, the smell of disinfectant was sharp and heavy. Doctors moved silently, their eyes avoiding his, their footsteps too synchronized. 'This is where memories are collected,' the doctor said. 'Not stored. Collected.' Ahmed acted—unplugging machines and shattering glass containers."
    },
    {
      num: 5,
      title: "The Memory Experiment",
      era: "Underground Genetic Facility",
      keys: 3,
      vocab: [
        { word: "Descent", def: "Downward movement or drop" },
        { word: "Implanted", def: "Embedded or inserted deeply" },
        { word: "Strategic", def: "Tactical and planned foresight" },
        { word: "Compatible", def: "Suitable for harmonious joining" }
      ],
      summary: "Descending into an underground facility, Ahmed discovers that his father Khaled Nour underwent genetic alteration to make memory transfer possible, creating a living shadow echo. Ahmed demolishes the DNA servers and returns home with strategic planning mastery.",
      excerpt: "Screens displayed rotating diagrams of DNA and human brains broken down into sections. Then he saw the name: Khaled Nour. 'Part of his genetic structure was altered to make him compatible with memory transfer,' the doctor whispered. Rage burned inside Ahmed..."
    },
    {
      num: 6,
      title: "The Doctor's Secret - Truth Beneath the Scalpel",
      era: "The Frozen Clinic",
      keys: 3,
      vocab: [
        { word: "Temporal", def: "Relating to time and duration" },
        { word: "Surveillance", def: "Continuous monitoring and observation" },
        { word: "Anomaly", def: "Irregularity or departure from baseline" },
        { word: "Synchronizing", def: "Aligning in perfect temporal harmony" }
      ],
      summary: "Ahmed arrives in a clinic where clocks are frozen. He finds medical files revealing he was tested as a child (Subject T-013) for 92% Temporal Resistance. His uncle appears, explaining why he kept Ahmed hidden from the shadow organization. As explosive attacks shake the facility, Ahmed's chronal combat powers ignite.",
      excerpt: "He flipped to the first page: Patient: Ahmed El-Sayed. Subject Code: T-013. Temporal Resistance Index: 92%. 'This wasn't medical care... this was surveillance.' Behind him, his uncle spoke: 'Because if you knew... you would've been taken long ago.'"
    },
    {
      num: 7,
      title: "The Pharaoh's Tomb",
      era: "Ancient Giza Pyramids",
      keys: 3,
      vocab: [
        { word: "Monumental", def: "Massive, enduring, and majestic" },
        { word: "Sarcophagus", def: "Ancient stone coffin" },
        { word: "Translucent", def: "Semi-transparent and glowing" },
        { word: "Dismantling", def: "Taking apart complex mechanisms" }
      ],
      summary: "Transported to golden Giza beneath monumental pyramids, Ahmed enters a ancient tomb filled with pressure plates and optical puzzles. Meeting a ghostly Pharaoh spirit, Ahmed proves his wisdom and patience, claiming a golden Time Key.",
      excerpt: "Around him rose massive stones carved with hieroglyphs. Torches lit themselves as he moved. Inside the sarcophagus chamber, a pharaoh spirit extended a translucent hand: 'Why do you disturb me?' 'I seek the truth of time,' Ahmed answered."
    },
    {
      num: 8,
      title: "The City of Lost Futures",
      era: "Alternate Reality Scar",
      keys: 0,
      vocab: [
        { word: "Flickering", def: "Shining unsteadily or wavering" },
        { word: "Déjà vu", def: "Feeling of having experienced the present before" },
        { word: "Consequence", def: "Outcome or inevitable result" },
        { word: "Unstable", def: "Volatile and prone to collapsing" }
      ],
      summary: "Ahmed walks through a city of lost futures—a scar of abandoned timelines where street signs glitch and store reflections lag. He confronts the running boy again, realizing the boy comes from a future Ahmed failed to save.",
      excerpt: "The sky wasn't one color—darker edges flickering like unfinished render. 'This is the place where every choice you didn't make lives,' the boy said softly. 'The futures you lost. The ones you never reached.'"
    },
    {
      num: 9,
      title: "The Watch That Knows Time",
      era: "City Desert Ruins & Tower",
      keys: 3,
      vocab: [
        { word: "Relics", def: "Sacred artifacts from ancient times" },
        { word: "Pivotal", def: "Crucial, turning-point significance" },
        { word: "Indifference", def: "Unconcerned or neutral stance" },
        { word: "Counterweight", def: "Balancing force or offset factor" }
      ],
      summary: "Ahmed's home experiences temporal pauses. Guided by Dr. Mounir Sadiq, Ahmed's family travels into the desert to locate the Keeper of the Watch inside a timeless tower. She surrenders the Chrono Watch, warning that every journey demands payment in change.",
      excerpt: "Dr. Mounir revealed the truth: 'An ancient artifact, the Chrono Key, shaped like the Egyptian Ankh. Broken intentionally across three eras.' At the tower, the Keeper extended her hand: 'Each journey through time will take something from you... You are now the counterweight.'"
    },
    {
      num: 10,
      title: "The First Fracture",
      era: "1972 Hospital & Present Desert",
      keys: 1,
      vocab: [
        { word: "Sterile", def: "Antiseptic, ultra-clean environment" },
        { word: "Integration", def: "Unification into a complete whole" },
        { word: "Unsettling", def: "Disturbing or disquieting" },
        { word: "Permanence", def: "Enduring stability and lasting state" }
      ],
      summary: "Ahmed travels to 1972 Cairo Hospital, witnessing his uncle Dr. Karim Khale
