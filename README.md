

import java.text.ParseException;
import java.text.SimpleDateFormat;
import java.util.ArrayList;
import java.util.Calendar;
import java.util.Date;
import java.util.HashMap;
import java.util.Iterator;
import java.util.List;
import java.util.Map;

/**
 * @description: TODO
 * @author primrose
 * @date 2020/10/30 11:28 上午
 * @version 1.0
 */
public class testDate {
    private static final String[] CHINESE_NUM = {"一", "二", "三", "四", "五", "六", "七", "八", "九", "十", "十一", "十二"};
//    private static final long[] LUNAR_CODE = new long[]{0x04bd8, 0x04ae0, 0x0a570,
//            0x054d5, 0x0d260, 0x0d950, 0x16554, 0x056a0, 0x09ad0, 0x055d2,
//            0x04ae0, 0x0a5b6, 0x0a4d0, 0x0d250, 0x1d255, 0x0b540, 0x0d6a0,
//            0x0ada2, 0x095b0, 0x14977, 0x04970, 0x0a4b0, 0x0b4b5, 0x06a50,
//            0x06d40, 0x1ab54, 0x02b60, 0x09570, 0x052f2, 0x04970, 0x06566,
//            0x0d4a0, 0x0ea50, 0x06e95, 0x05ad0, 0x02b60, 0x186e3, 0x092e0,
//            0x1c8d7, 0x0c950, 0x0d4a0, 0x1d8a6, 0x0b550, 0x056a0, 0x1a5b4,
//            0x025d0, 0x092d0, 0x0d2b2, 0x0a950, 0x0b557, 0x06ca0, 0x0b550,
//            0x15355, 0x04da0, 0x0a5d0, 0x14573, 0x052d0, 0x0a9a8, 0x0e950,
//            0x06aa0, 0x0aea6, 0x0ab50, 0x04b60, 0x0aae4, 0x0a570, 0x05260,
//            0x0f263, 0x0d950, 0x05b57, 0x056a0, 0x096d0, 0x04dd5, 0x04ad0,
//            0x0a4d0, 0x0d4d4, 0x0d250, 0x0d558, 0x0b540, 0x0b5a0, 0x195a6,
//            0x095b0, 0x049b0, 0x0a974, 0x0a4b0, 0x0b27a, 0x06a50, 0x06d40,
//            0x0af46, 0x0ab60, 0x09570, 0x04af5, 0x04970, 0x064b0, 0x074a3,
//            0x0ea50, 0x06b58, 0x055c0, 0x0ab60, 0x096d5, 0x092e0, 0x0c960,
//            0x0d954, 0x0d4a0, 0x0da50, 0x07552, 0x056a0, 0x0abb7, 0x025d0,
//            0x092d0, 0x0cab5, 0x0a950, 0x0b4a0, 0x0baa4, 0x0ad50, 0x055d9,
//            0x04ba0, 0x0a5b0, 0x15176, 0x052b0, 0x0a930, 0x07954, 0x06aa0,
//            0x0ad50, 0x05b52, 0x04b60, 0x0a6e6, 0x0a4e0, 0x0d260, 0x0ea65,
//            0x0d530, 0x05aa0, 0x076a3, 0x096d0, 0x04bd7, 0x04ad0, 0x0a4d0,
//            0x1d0b6, 0x0d250, 0x0d520, 0x0dd45, 0x0b5a0, 0x056d0, 0x055b2,
//            0x049b0, 0x0a577, 0x0a4b0, 0x0aa50, 0x1b255, 0x06d20, 0x0ada0};
private static final long[] LUNAR_CODE = new long[]{

        0x04bd8, 0x04ae0, 0x0a570, 0x054d5, 0x0d260, 0x0d950, 0x16554, 0x056a0, 0x09ad0, 0x055d2,//1900-1909

        0x04ae0, 0x0a5b6, 0x0a4d0, 0x0d250, 0x1d255, 0x0b540, 0x0d6a0, 0x0ada2, 0x095b0, 0x14977,//1910-1919

        0x04970, 0x0a4b0, 0x0b4b5, 0x06a50, 0x06d40, 0x1ab54, 0x02b60, 0x09570, 0x052f2, 0x04970,//1920-1929

        0x06566, 0x0d4a0, 0x0ea50, 0x16a95, 0x05ad0, 0x02b60, 0x186e3, 0x092e0, 0x1c8d7, 0x0c950,//1930-1939

        0x0d4a0, 0x1d8a6, 0x0b550, 0x056a0, 0x1a5b4, 0x025d0, 0x092d0, 0x0d2b2, 0x0a950, 0x0b557,//1940-1949

        0x06ca0, 0x0b550, 0x15355, 0x04da0, 0x0a5b0, 0x14573, 0x052b0, 0x0a9a8, 0x0e950, 0x06aa0,//1950-1959

        0x0aea6, 0x0ab50, 0x04b60, 0x0aae4, 0x0a570, 0x05260, 0x0f263, 0x0d950, 0x05b57, 0x056a0,//1960-1969

        0x096d0, 0x04dd5, 0x04ad0, 0x0a4d0, 0x0d4d4, 0x0d250, 0x0d558, 0x0b540, 0x0b6a0, 0x195a6,//1970-1979

        0x095b0, 0x049b0, 0x0a974, 0x0a4b0, 0x0b27a, 0x06a50, 0x06d40, 0x0af46, 0x0ab60, 0x09570,//1980-1989

        0x04af5, 0x04970, 0x064b0, 0x074a3, 0x0ea50, 0x06b58, 0x05ac0, 0x0ab60, 0x096d5, 0x092e0,//1990-1999

        0x0c960, 0x0d954, 0x0d4a0, 0x0da50, 0x07552, 0x056a0, 0x0abb7, 0x025d0, 0x092d0, 0x0cab5,//2000-2009

        0x0a950, 0x0b4a0, 0x0baa4, 0x0ad50, 0x055d9, 0x04ba0, 0x0a5b0, 0x15176, 0x052b0, 0x0a930,//2010-2019

        0x07954, 0x06aa0, 0x0ad50, 0x05b52, 0x04b60, 0x0a6e6, 0x0a4e0, 0x0d260, 0x0ea65, 0x0d530,//2020-2029

        0x05aa0, 0x076a3, 0x096d0, 0x04afb, 0x04ad0, 0x0a4d0, 0x1d0b6, 0x0d250, 0x0d520, 0x0dd45,//2030-2039

        0x0b5a0, 0x056d0, 0x055b2, 0x049b0, 0x0a577, 0x0a4b0, 0x0aa50, 0x1b255, 0x06d20, 0x0ada0,//2040-2049

        0x14b63, 0x09370, 0x049f8, 0x04970, 0x064b0, 0x168a6, 0x0ea50, 0x06b20, 0x1a6c4, 0x0aae0,//2050-2059

        0x092e0, 0x0d2e3, 0x0c960, 0x0d557, 0x0d4a0, 0x0da50, 0x05d55, 0x056a0, 0x0a6d0, 0x055d4,//2060-2069

        0x052d0, 0x0a9b8, 0x0a950, 0x0b4a0, 0x0b6a6, 0x0ad50, 0x055a0, 0x0aba4, 0x0a5b0, 0x052b0,//2070-2079

        0x0b273, 0x06930, 0x07337, 0x06aa0, 0x0ad50, 0x14b55, 0x04b60, 0x0a570, 0x054e4, 0x0d160,//2080-2089

        0x0e968, 0x0d520, 0x0daa0, 0x16aa6, 0x056d0, 0x04ae0, 0x0a9d4, 0x0a2d0, 0x0d150, 0x0f252//2090-2099

};

    private int mYear;
    private int mMonth;
    private int mDay;
    private boolean mLeap;

    /**
     * constructor
     *
     * @param cal Calendar
     */
    public testDate(Calendar cal) {
        @SuppressWarnings("unused")
        int yearCyl, monCyl, dayCyl;
        int leapMonth = 0;

        Date baseDate = null;
        try {
            SimpleDateFormat chineseDateFormat = new SimpleDateFormat("yyyy-MM-dd");
            baseDate = chineseDateFormat.parse("1900-1-31");
        } catch (ParseException e) {
            //throw e;
        }

        // 求出和1900年1月31日相差的天数
        int offset = (int) ((cal.getTime().getTime() - baseDate.getTime()) / 86400000L);
        dayCyl = offset + 40;
        monCyl = 14;

        // 用offset减去每农历年的天数
        // 计算当天是农历第几天
        // i最终结果是农历的年份
        // offset是当年的第几天
        int iYear, daysOfYear = 0;
        for (iYear = 1900; iYear < 2050 && offset > 0; iYear++) {
            daysOfYear = yearDays(iYear);
            offset -= daysOfYear;
            monCyl += 12;
        }
        if (offset < 0) {
            offset += daysOfYear;
            iYear--;
            monCyl -= 12;
        }

        // 农历年份
        mYear = iYear;
        yearCyl = iYear - 1864;
        // 闰哪个月,1-12
        leapMonth = leapMonth(iYear);

        mLeap = false;
        // 用当年的天数offset,逐个减去每月（农历）的天数，求出当天是本月的第几天
        int iMonth, daysOfMonth = 0;
        for (iMonth = 1; iMonth < 13 && offset > 0; iMonth++) {
            // 闰月
            if (leapMonth > 0 && iMonth == (leapMonth + 1) && !mLeap) {
                --iMonth;
                mLeap = true;
                daysOfMonth = leapDays(mYear);
            } else {
                daysOfMonth = monthDays(mYear, iMonth);
            }
            offset -= daysOfMonth;
            // 解除闰月
            if (mLeap && iMonth == (leapMonth + 1)) {
                mLeap = false;
            }
            if (!mLeap) {
                monCyl++;
            }
        }

        // offset为0时，并且刚才计算的月份是闰月，要校正
        if (offset == 0 && leapMonth > 0 && iMonth == leapMonth + 1) {
            if (mLeap) {
                mLeap = false;
            } else {
                mLeap = true;
                --iMonth;
                --monCyl;
            }
        }

        // offset小于0时，也要校正
        if (offset < 0) {
            offset += daysOfMonth;
            --iMonth;
            --monCyl;
        }

        mMonth = iMonth;
        mDay = offset + 1;
    }

    /**
     * 传回农历 y年的总天数
     *
     * @param y
     * @return
     */
    final private static int yearDays(int y) {
        int i, sum = 348;
        for (i = 0x8000; i > 0x8; i >>= 1) {
            if ((LUNAR_CODE[y - 1900] & i) != 0) {
                sum += 1;
            }
        }
        return (sum + leapDays(y));
    }

    /**
     * 传回农历 y年闰月的天数
     */
    final private static int leapDays(int y) {
        if (leapMonth(y) != 0) {
            if ((LUNAR_CODE[y - 1900] & 0x10000) != 0) {
                return 30;
            } else {
                return 29;
            }
        } else {
            return 0;
        }
    }

    /**
     * 传回农历 y年闰哪个月 1-12 , 没闰传回 0
     */
    final private static int leapMonth(int y) {
        return (int) (LUNAR_CODE[y - 1900] & 0xf);
    }

    /**
     * 传回农历 y年m月的总天数
     */
    final private static int monthDays(int y, int m) {
        if ((LUNAR_CODE[y - 1900] & (0x10000 >> m)) == 0) {
            return 29;
        } else {
            return 30;
        }
    }

    /**
     * 传回干支, 0=甲子
     *
     * @param num 公历日期
     * @return 传回干支, 0=甲子
     */
    final private static String cyclicalm(int num) {
        final String[] gan = new String[]{"甲", "乙", "丙", "丁", "戊", "己", "庚",
                "辛", "壬", "癸"};
        final String[] zhi = new String[]{"子", "丑", "寅", "卯", "辰", "巳", "午",
                "未", "申", "酉", "戌", "亥"};
        return (gan[num % 10] + zhi[num % 12]);
    }

    /**
     * 获取农历日期
     *
     * @param day 公历日期
     * @return 农历日期字符串
     */
    public static String getChinaDayString(int day) {
        String[] chineseTen = {"初", "十", "廿", "卅"};
        int n = day % 10 == 0 ? 9 : day % 10 - 1;
        if (day > 30) {
            return "";
        }
        if (day == 10) {
            return "初十";
        } else {
            return chineseTen[day / 10] + CHINESE_NUM[n];
        }
    }

    /**
     * 传回干支, 0=甲子
     */
    final public String cyclicalYear() {
        int num = mYear - 1900 + 36;
        return (cyclicalm(num));
    }

    /**
     * 农历y年的生肖
     */
    final public String zodiacYear() {
        final String[] zodiac = new String[]{"鼠", "牛", "虎", "兔", "龙", "蛇", "马", "羊", "猴", "鸡", "狗", "猪"};
        return zodiac[(mYear - 4) % 12];
    }

    @Override
    public String toString() {
        return cyclicalYear() + "年" + (mLeap ? "闰" : "") + CHINESE_NUM[mMonth - 1] + "月" + getChinaDayString(mDay);
    }

    public static void main(String[] args) {
        List<Map<String,String>> result=new ArrayList();
        //农历/公历日期计算

        for (int i=0;i<36600;i++) {
            Calendar instance = Calendar.getInstance();
            instance.add(Calendar.DAY_OF_YEAR,i-365*90);
            testDate lunarDay = new testDate(instance);
            String day = lunarDay.toString();
            long timeInMillis = instance.getTimeInMillis();
            SimpleDateFormat sdf = new SimpleDateFormat("yyyy-MM-dd HH:mm:ss");
            String format = sdf.format(timeInMillis);
            if(day.contains("十二月初八")){
                if(format.contains("-01-13")){
                    //       if(format.contains("-01-13")){
                HashMap<String, String> obj = new HashMap<>();

                System.out.println(format+"  "+day);
                obj.put(format,day);
                result.add(obj);
            }

        }


    }
}}
